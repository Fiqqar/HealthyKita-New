<template>
<div>
<p>sedang mengarahkan anda....</P>
</div>
</template>  
      <script>
        import Cookies from 'js-cookie'
        import { onMounted } from 'vue'
        import { useRoute } from 'vue-router'
        import localforage from 'localforage'

        export default {
            name: 'oauthGoogle',

            setup() {
                const route = useRoute();
                let encription = localforage.createInstance({
                   name: "KeyDatabase"

            })
            
                onMounted(() => {
                    const accessToken = route.query.accessToken;
                const email = route.query.email
                    if (accessToken) {
                                const now = new Date()
                                localStorage.setItem("oauth", accessToken);
                                Cookies.set('tokenUser', email, { expires:  now.setTime(now.getTime() + (1 * 60 * 60 * 1000)), path: '/' })
                        }
                    let encKey = route.query.encKey;
                    let ivKey = route.query.ivKey;

                    if(encKey && ivKey){
                    encKey = encKey.split(',').map(Number);
                    ivKey = ivKey.split(',').map(Number);
                    }
                
                    if (encKey && ivKey) {
                        encription.setItem("encKey", encKey)
                        encription.setItem("ivKey", ivKey)
                    }
                    setTimeout(() => {
                        window.location.href = `http://localhost:8080/home`
                    }, 5000);

                })
            },
        };
        </script>
