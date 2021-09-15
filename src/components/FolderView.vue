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

// body{background: #edf2f7;}
// details{
//   display:block;
//   margin-bottom: .5rem;
// }
// summary::-webkit-details-marker{display:none;}
// summary::-moz-list-bullet{list-style-type:none;}
// summary::marker{display:none;} 
// summary {
//    padding: .3em .5em;
//    display:inline-block;
//    font-size:1.4em;
//    cursor: pointer;
// }
// summary:before {  
//   content: "+";
//   margin-right: .3em;
// }
// details[open] > summary:before {
//   content: "–";
// }

// summary ~ * {
//    padding:0 1em;
// }

 body{background: #edf2f7;}
details{
  // display:block;
  background: #fff;
  width:300px;
  box-shadow: 0 10px 15px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  border-radius: 8px;
  margin-bottom: 1.5rem;
}
summary::-webkit-details-marker{display:none;}
summary::-moz-list-bullet{list-style-type:none;}
summary::marker{display:none;} 
summary {
   display:block;
   padding: .3em 1em .3em .9em;
   border-bottom: 1px solid #e2e8f0;
   font-size:1.4em;
   cursor: pointer;
   position: relative;
}
summary:before {  
  top: .4em;
  right: .3em;
  color: transparent;
  background: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij48cGF0aCBkPSJNMTYuNTkgOC41OUwxMiAxMy4xNyA3LjQxIDguNTkgNiAxMGw2IDYgNi02eiIvPjxwYXRoIGQ9Ik0wIDBoMjR2MjRIMHoiIGZpbGw9Im5vbmUiLz48L3N2Zz4=") no-repeat 50% 50% / 1em 1em;
  width: 1em;
  height: 1em;  
  content: "";
  position: absolute;
  transition: transform .5s;
}
details[open] > summary:before {
  transform: scale(1,-1);
}
summary ~ * {
   padding: 0 1em 10px 1.4em;
}
details[open] summary ~ *{ 
  animation: sweep .5s ease-in-out;
}
@keyframes sweep {
  0%    {opacity: 0;}
  100%  {opacity: 1;}
}
summary:focus {
  // outline: solid red 2px;
  box-shadow: inset 0 0 1px rgba(0,0,0,0.3), inset 0 0 2px rgba(0,0,0,0.3);
}
</style>
