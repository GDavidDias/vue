<script>
    export default{
        emits:["onTagChange"],
        data(){
            return{
                currentValue:"",
                tags: [],
            };
        },

        methods:{
            handleKeyDown(e){
                if(e.key=="Backspace" && this.currentValue == ""){
                    this.tags.pop();
                    //this.OnTagChange(this.tags);
                    this.$emit("onTagChange", this.tags);
                }
            },
            handleSubmit(){
                if(this.currentValue!=""){
                    const existe = this.tags.some((item)=>item==this.currentValue);
                    if(!existe){
                        this.tags.push(this.currentValue);
                        this.currentValue="";
                        //this.OnTagChange(this.tags);
                        this.$emit("onTagChange", this.tags);
                    };
                };
            },
            deleteTag(tag){
                this.tags = this.tags.filter((item)=>item!=tag);
                //this.OnTagChange(this.tags);
                this.$emit("onTagChange", this.tags);
            },
        },
    }

</script>

<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }} <button @click="deleteTag(tag)">X</button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit">
            <input class="input" type="text" v-model="currentValue" @keydown="handleKeyDown">
        </form>
    </div>
</template>

<style scoped>
.inputTag{
    display: inline-flex;
    align-items: center;
    border: solid 1px #6153cb;
    border-radius: 3px;
    height: 43px;
    width: 50vw;
}
.tags{
    display: flex;
    gap: 3px;
    padding: 5px;
}
.tags .tag {
    display: flex;
    padding: 5px;
    border: solid 1px #cab0ff;
    gap: 5px;
    align-content: center;
    border-radius: 3px;
}

.inputTag form{
    display: inline-flex;
}

.inputTag .input{
    border: none;
    outline: none;
    padding: 0.5px;
    background-color: transparent;
}
.tag button{
    background-color: transparent;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.tag button:hover{
    background-color: #eee;
}
</style>