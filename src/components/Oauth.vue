<script>
import Cookies from 'js-cookie'
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';

export default {
    name: 'oauthGoogle',

    setup() {
        const route = useRoute();

        onMounted(() => {
            let encKey = route.query.encKey;
            let ivKey = route.query.ivKey;

            encKey = encKey.split(',').map(Number);
            ivKey = ivKey.split(',').map(Number);


         
            const accessToken = route.query.accessToken;
            const email = route.query.email

            if (accessToken) {
                const now = new Date()
                localStorage.setItem("oauth", accessToken);
                Cookies.set('tokenUser', now.setTime(now.getTime() + (1 * 60 * 60 * 1000)), { expires: now, path: '/' });
            }

            if (encKey && ivKey) {
                const request = indexedDB.open('KeyDatabase', 1);
        
        request.onerror = (event) => {
            console.error('IndexedDB error:', event.target.error);
        };

        request.onupgradeneeded = (event) => {
            const db = event.target.result;
            if (!db.objectStoreNames.contains('keys')) {
                db.createObjectStore('keys', { keyPath: 'id' });
            }
        };

        request.onsuccess = (event) => {
            const db = event.target.result;
            const transaction = db.transaction(['keys'], 'readwrite');
            const store = transaction.objectStore('keys');

            store.put({ id: 'encKey', value: encKey });
            store.put({ id: 'ivKey', value: ivKey });

            transaction.oncomplete = () => {
                console.log('Keys stored successfully in IndexedDB');
                window.location.href = `http://localhost:8080/home`;
            };

            transaction.onerror = (event) => {
                console.error('Error:', event.target.error);
            };
        };
                //please store this at indexedDb of encKey and ivKey
            } else {
                console.log('encKey or ivKey is missing.');
            }
        });

    },
};
</script>

<style scoped></style>
