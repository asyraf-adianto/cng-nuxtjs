<template>
    <div class="select-none">
        <div :class="this.config.ring" class="transition duration-300 flex flex-row justify-between items-center content-center bg-white rounded-xl h-10 shadow-md pl-4 gap-2">
            <input  @focus="toggleActivate" @blur="toggleBlur" type="text" id="data" v-model="data.search" :placeholder="this.placeholder" class="cursor-pointer h-6 bg-transparent focus:outline-none" readonly>
            <div class="flex flex-row justify-between items-center content-center gap-2" >
                <button @click="removeData" :class="this.config.btremove" class="fas fa-times-circle"></button>
                <button @click="toggleSwitch" :class="this.config.icon" class="fas h-10 w-10 text-2xl bg-blue-500 rounded-xl text-white"></button>
            </div>
        </div>
        <div @mouseenter="optionEnter" @mouseleave="optionExit" :class="this.config.open" class="transition duration-300 mt-2.5 flex flex-col justify-start items-start bg-white rounded-xl shadow-md gap-1 overflow-hidden">
            <button @click="selectData(option)" class="text-left h-10 w-full hover:bg-blue-500 hover:text-white px-4 py-2 "
                v-for="option of filteredOption" :key="option.id">
                {{ option.title }}
            </button>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            selection: {
                type: Array,
                default: [
                    {
                        "id":1,
                        "title":"Option A"
                    },
                    {
                        "id":2,
                        "title":"Option E"
                    },
                    {
                        "id":3,
                        "title":"Option U"
                    }
                ]
            },
            placeholder: {
                type: String,
                default: "select"
            }
        },
        data() {
            return {
                data: {
                    search:'',
                    selected:''
                },
                config:{
                    open: 'hidden',
                    icon: 'fa-caret-right',
                    ring: '',
                    canBlur: false,
                    btremove: ' invisible '
                },
            }
        },
        computed: {
            filteredOption() {
                return this.selection.filter(post => {
                    return post.title.toLowerCase().includes(this.data.search.toLowerCase())
                })
            }
        },
        methods: {
            toggleActivate() {
                this.config.open = '';
                this.config.ring = 'ring-offset-1 ring'; 
                this.config.icon = 'fa-caret-down' ;
            },
            toggleBlur(){
                (this.config.canBlur == true) ? this.toggleDeactivate(): '' ;
            },
            toggleDeactivate(){
                this.config.open = 'hidden';
                this.config.ring = 'visible'; 
                this.config.icon = 'fa-caret-right' ;
            },
            toggleSwitch(){
                (this.config.byBlur == true) ? '' : 
                (this.config.open == 'hidden') ? this.toggleActivate() : this.toggleDeactivate();
                this.config.byBlur = (this.config.byBlur == true) ? false : false;
            },
            selectData(d){
                this.data.selected = d;
                this.data.search = this.data.selected.title;
                this.config.btremove = '';
                this.$emit("getData",this.data.selected);
                this.toggleDeactivate();
            },
            optionEnter(){
                this.config.canBlur = false;
            },
            optionExit(){
                this.config.canBlur = true;
            },
            removeData(){
                this.data.selected = '';
                this.data.search = '';
                this.config.btremove = ' invisible '
            },
            setFocus(){
                this.$refs.inputForm.focus();
            }
        }
    }
</script>