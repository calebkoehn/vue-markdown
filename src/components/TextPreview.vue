<template>
    <div class="right-body">
        <div id="right-body-header">
            <h4 class="preview-text">Preview</h4>
            <img src="../assets/icon-show-preview.svg" alt="show icon">
        </div>
        <div class="preview" v-html="compiledPreview"></div>
    </div>
</template>

<script> 
import {marked} from 'marked';
    export default {
        
        name: 'TextPreview',
        props: {
            input: {
                type: String,
                default: "",
            }
        },
        computed: {
            compiledPreview: function () {
                return marked(this.input, {sanitizer: true, headerIds: false});
            }
        },
    }
</script>

<style>
.right-body {
    float: right;
    width: 99%;
    padding-right: 15px;
}
#right-body-header {
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
    padding-right: 10px;
}
.preview {
    background-color: black;
    color: grey;
    height: 100%;
    width: 100%;
    border: none;
    margin-top: 2%;
    padding-left: 3px;
}
@media only screen and (max-width: 710px){
    div.right-body{
        display: none;
    }
}
@media only screen and (max-width: 710px){
    div.preview{
        display: none;
    }
}
@media only screen and (max-width: 710px){
    h4.preview-text{
        display: none;
    }
}

</style>