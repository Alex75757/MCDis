<template>
  <details> 
    <summary class="folder">{{name}}</summary>
  
  <slot v-for="folder in folders" >
    <FolderView :name="folder.name" :folders="folder.folders" :files="folder.files"/>
  </slot>
  <slot v-for="file in files">
    <FileView :name="file.name"/>
  </slot>
  </details>
</template>

<script>
import FileView from "./FileView";
export default {
  name: 'FolderView',
  components: {FileView},
  props: {
    name: String,
    folders:Array,
    files:Array
 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.folder{
  color: orangered;
}

body{background: #edf2f7;}
details{
  display:block;
  margin-bottom: .5rem;
}
summary::-webkit-details-marker{display:none;}
summary::-moz-list-bullet{list-style-type:none;}
summary::marker{display:none;} 
summary {
   padding: .3em .5em;
   display:inline-block;
   font-size:1.4em;
   cursor: pointer;
}
summary:before {  
  content: "+";
  margin-right: .3em;
}
details[open] > summary:before {
  content: "–";
}

summary ~ * {
   padding:0 1em;
}

</style>
