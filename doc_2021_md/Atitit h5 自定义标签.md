Atitit h5 自定义标签 Web Components之自定义HTML标签


<script>
    class WordCount extends HTMLDivElement {
  constructor() {
    // Always call super first in constructor
    super();

    // Element functionality written in here

   //...
  }
}

customElements.define('mwlw', WordCount);
</script>
<style>
mwlw{
    display:block;
    height:100px;
    background-color:blue;
}
    </style>
<mwlw>
111
</mwlw>

