<template>
    <div class="z-50 flex flex-col justify-start text-left content-start items-start py-10">
        <div>
            <div  
                class="transition duration-300 flex flex-row justify-end items-center 
                content-center bg-white rounded-xl h-10 shadow-md pl-4 gap-2"
                :class="this.config.ring">
                <input ref="input" type="text" id="data" :value="this.data.selected.title" placeholder="search" 
                    @focus="toggleActivate" @blur="toggleBlur" 
                    class=" h-6" />
                <button @click="removeData" 
                    class="fas fa-times-circle"></button>
                <button @click="toggleSwitch" :class="this.config.icon" 
                    class="fas h-10 w-10 text-2xl bg-blue-500 rounded-xl 
                    text-white"></button>
            </div>
            <div 
                :class="this.config.open" 
                class=" transition duration-300 mt-2.5 flex flex-col 
                justify-start items-start bg-white rounded-xl shadow-md 
                gap-1 overflow-hidden">
                <button 
                    @click="selectData(data)"
                    v-for="data of data.filtered" :key="data.id" 
                    class="text-left h-10 w-full hover:bg-blue-500 hover:text-white px-4 py-2 ">
                    {{ data.title }}
                </button>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                data:{
                    selected:'',
                    basic:[
                        {
                            "id":1,
                            "title":"Option 1"
                        },
                        {
                            "id":2,
                            "title":"Option 2"
                        },
                        {
                            "id":3,
                            "title":"Option 3"
                        }
                    ],
                    filtered:[],
                },
                config:{
                    open: 'invisible',
                    icon: 'fa-caret-right',
                    ring: '',
                    byBlur: false
                },
            }
        },
        methods: {
            toggleActivate() {
                this.config.open = '';
                this.config.ring = 'ring-offset-1 ring'; 
                this.config.icon = 'fa-caret-down' ;
            },
            toggleBlur(){
                this.config.byBlur = true;
                this.toggleDeactivate();
            },
            toggleDeactivate(){
                this.config.open = 'invisible';
                this.config.ring = 'visible'; 
                this.config.icon = 'fa-caret-right' ;
            },
            toggleSwitch(){
                (this.config.byBlur == true) ? '' : 
                (this.config.open == 'invisible') ? this.toggleActivate() : this.toggleDeactivate();
                this.config.byBlur = (this.config.byBlur == true) ? false : false;
            },
            selectData(d){
                this.data.selected = d;
                this.$emit("getData",this.data.selected);
                this.toggleDeactivate();
            },
            removeData(){
                this.data.selected = '';
                this.$emit("deleteData",this.data.selected);
                this.toggleDeactivate();
            },
            setFocus(){
                this.$refs.input.focus();
            }
        },
        async fetch() {
            this.data.filtered = this.data.basic
        },
    }
</script>