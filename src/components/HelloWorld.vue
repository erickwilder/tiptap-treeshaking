<template>
  <div class="container">
    <editor
      :extensions="extensions">
      <div
        slot="menubar"
        slot-scope="{ nodes, marks }"
        class="menubar">
        <div v-if="nodes && marks">
          <button @click="marks.bold.command">
            B
          </button>
          <button
            :class="{ 'active': marks.italic.active() }"
            @click="marks.italic.command"
          >
            I
          </button>
          <button
            :class="{ 'active': marks.strike.active() }"
            @click="marks.strike.command"
          >
            <em class="strike">S</em>
          </button>
          <button
            :class="{ 'active': marks.underline.active() }"
            @click="marks.underline.command"
          >
            U
          </button>
          <button
            :class="{ 'active': nodes.paragraph.active() }"
            @click="nodes.paragraph.command"
          >
            P
          </button>
          <button
            :class="{ 'active': nodes.heading.active({ level: 1 }) }"
            @click="nodes.heading.command({ level: 1 })"
          >
            H1
          </button>
          <button
            :class="{ 'active': nodes.heading.active({ level: 2 }) }"
            @click="nodes.heading.command({ level: 2 })"
          >
            H2
          </button>
          <button
            :class="{ 'active': nodes.heading.active({ level: 3 }) }"
            @click="nodes.heading.command({ level: 3 })"
          >
            H3
          </button>
          <button
            :class="{ 'active': nodes.bullet_list.active() }"
            @click="nodes.bullet_list.command"
          >
            UL
          </button>
          <button
            :class="{ 'active': nodes.ordered_list.active() }"
            @click="nodes.ordered_list.command"
          >
            OL
          </button>
        </div>
      </div>
      <div
        slot="content"
        slot-scope="props"
        class="email-visual-editor-content__content">
        <h1>Hello Tiptap</h1>
        <p>Please, run `npm run build:analyze` and check the bundled highlight.js even tough it is not used here anywhere.</p>
      </div>
    </editor>
  </div>
</template>

<script>
import { Editor } from 'tiptap'
import {
  BulletListNode,
  HardBreakNode,
  HeadingNode,
  ListItemNode,
  OrderedListNode,
  BoldMark,
  ItalicMark,
  StrikeMark,
  UnderlineMark
} from 'tiptap-extensions'

export default {
  name: 'HelloWorld',
  components: {
    Editor
  },
  data () {
    return {
      extensions: [
        new BulletListNode(),
        new HardBreakNode(),
        new HeadingNode({ maxLevel: 3 }),
        new ListItemNode(),
        new OrderedListNode(),
        new BoldMark(),
        new ItalicMark(),
        new StrikeMark(),
        new UnderlineMark()
      ]
    }
  }
}
</script>

<style scoped>
.container {
  border: 1px solid #cfcfcf;
}
button {
  background: #fff;
  color: #333;
}
button.active {
  background: rgba(135, 38, 173, 0.5);
  color: #fff;
}
.strike {
  text-decoration: line-through;
  font-style: normal;
}
</style>
