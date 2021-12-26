<template>
    <div class="select-none">
        <div :class="this.config.ring" class="transition duration-300 flex flex-row justify-between items-center content-center bg-white rounded-xl h-10 shadow-md pl-4 gap-2">
            <input @keydown="checkData" @mousenter="optionEnter" @mouseleave="optionExit" @focus="toggleActivate" @blur="toggleBlur" type="text" id="data" v-model="data.input" :placeholder="this.placeholder" class="cursor-text h-6 bg-transparent focus:outline-none" />
            <div class="flex flex-row justify-between items-center content-center gap-2 pr-4" >
                <button @click="removeData" :class="this.config.btremove" class="fas fa-times-circle"></button>
            </div>
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
                default: "search"
            }
        },
        data() {
            return {
                data: {
                    input:'',
                    selected:''
                },
                config:{
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
                this.config.ring = 'ring-offset-1 ring'; 
                this.config.icon = 'fa-caret-down' ;
            },
            toggleBlur(){
                (this.config.canBlur == true) ? this.toggleDeactivate(): '' ;
            },
            toggleDeactivate(){
                this.config.ring = 'visible'; 
                this.config.icon = 'fa-caret-right' ;
            },
            checkData(){
                this.config.btremove = (this.data.input == '') ? ' invisible ' : '' ;
                this.$emit("getData",this.data.input);
            },
            optionEnter(){
                this.config.canBlur = false;
            },
            optionExit(){
                this.config.canBlur = true;
            },
            removeData(){
                this.data.input = '';
                this.config.btremove = ' invisible '
            },
            setFocus(){
                this.$refs.inputForm.focus();
            }
        }
    }
</script>