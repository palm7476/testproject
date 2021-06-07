<template>
    <div>
        <div style="margin: 10px;" class="btn-group" role="group" aria-label="Basic example">
            <button type="button" class="btn btn-danger" @click="logout()">Logout</button>
            <button type="button" class="btn btn-link">{{ datas.username }}</button>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            
            datas : []    

            }
    },
    methods: {

        logout(){
            axios.post('/logout',{
                
            }).then((response)=> {
                if(response.data == 'success'){
                window.location.href = '/login'
                }
            })
        },
        getdata(){
            axios.get('/showuserlogin',{

            }).then((response)=> {
                this.datas=response.data
            })
        }
    },
    created(){
        this.getdata()
    }
}
</script>