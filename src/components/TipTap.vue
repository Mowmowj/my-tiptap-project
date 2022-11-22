<template>
  <div v-if="editor">
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import StarterKit from "@tiptap/starter-kit";
import { Editor, EditorContent } from "@tiptap/vue-3";

import DraggableItem from "./DraggableItem.js";

export default {
  components: {
    EditorContent,
  },

  data() {
    return {
      editor: null,
    };
  },

  mounted() {
    this.editor = new Editor({
      extensions: [StarterKit, DraggableItem],
      content: `
        <p>This is a boring paragraph.</p>
        <div data-type="draggable-item">
          <div
          >1Followed by a fancy draggable item.</div>
        </div>
        <div data-type="draggable-item">
          <div 
          >2Followed by a fancy draggable item.</div>
        </div>
        <div data-type="draggable-item">
          <div 
          >3Followed by a fancy draggable item</div>
        </div>
      `,
    });
  },

  beforeUnmount() {
    this.editor.destroy();
  },
};
</script>
