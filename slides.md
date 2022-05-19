---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  Presentation with the Skill use-in JavaScript.
drawings:
  persist: false
---

# JavaScript Skill

Presentation with the Skill use-in JavaScript

@[zhang13pro](https://github.com/zhang13pro)

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Start <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/zhang13pro" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!-- https://juejin.cn/post/6844903838449664013 -->

---

# String Skill

```ts {monaco}
type StrOrNum = string | number

const ThousandNum = (num: number): StrOrNum => {
  return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
}
console.log(ThousandNum(20190214))
```

<!-- <iframe width="560" height="600" src="https://www.typescriptlang.org/play" /> -->
