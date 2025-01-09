<script>
import Cookies from 'js-cookie'
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';

export default {
    name: 'oauthGoogle',

    setup() {
        const route = useRoute();

        onMounted(() => {
            const encKey = route.query.encKey;
            const ivKey = route.query.ivKey;
            const accessToken = route.query.accessToken;
            const email = route.query.email

            if (accessToken) {
                localStorage.setItem("oauth", accessToken);
                Cookies.set('tokenUser', email, { expires: 3500, path: '/' });
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

            window.location.href = `http://localhost:8080/home`
        });

    },
};
</script>

<style scoped></style>