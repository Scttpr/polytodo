<script setup lang="ts">
const items = ref([] as { content: string; checked: boolean }[])
const item = ref('')

const addItem = () => {
  if (item.value)
    items.value.push({ content: item.value, checked: false })

  item.value = ''
}

const checkItem = (index) => {
  items.value = items.value.map((item, i) => {
    if (i === index)
      item.checked = !item.checked

    return item
  })
}

const removeItem = (index) => {
  items.value.splice(index, 1)
}
</script>

<template>
  <h1 class="text-4xl text-lime-600 font-bold my-8">
    POLYTODO
  </h1>

  <form class="flex flex-col w-1/2 mx-auto justify-center items-center" @submit.prevent="addItem">
    <input
      id="item"
      v-model="item"
      class="w-full py-2 px-4 rounded text-black bg-gray-300"
      name="item"
      type="text"
      placeholder="Add item"
    >
    <button class="w-full py-2 px-4 my-2 bg-lime-600 rounded" type="submit">
      Add item to list
    </button>
  </form>

  <section class="w-1/2 mx-auto">
    <ul class="flex flex-col justify-start items-start">
      <Item
        v-for="({ checked, content }, index) in items"
        :key="`polytodo-item${index}`"
        :content="content"
        :index="index"
        :checked="checked"
        @remove="removeItem"
        @check="checkItem"
      />
    </ul>
  </section>
</template>

<route lang="yaml">
</route>
