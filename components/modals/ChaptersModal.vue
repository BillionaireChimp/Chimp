<template>
  <modals-modal v-model="show" :width="300" height="100%">
    <div class="w-full h-full overflow-hidden absolute top-0 left-0 flex items-center justify-center" @click="show = false">
      <div class="w-full overflow-x-hidden overflow-y-auto bg-primary rounded-lg border border-white border-opacity-20" style="max-height: 75%" @click.stop>
        <ul class="h-full w-full" role="listbox" aria-labelledby="listbox-label">
          <template v-for="chapter in chapters">
            <li :key="chapter.id" class="text-gray-50 select-none relative py-3 cursor-pointer hover:bg-black-400" role="option" @click="clickedOption(chapter)">
              <div class="flex items-center justify-center px-3">
                <span class="font-normal block truncate text-lg">{{ chapter.title }}</span>
                <div class="flex-grow" />
                <span class="font-mono text-gray-300">{{ $secondsToTimestamp(chapter.start) }}</span>
              </div>
            </li>
          </template>
        </ul>
      </div>
    </div>
  </modals-modal>
</template>

<script>
export default {
  props: {
    value: Boolean,
    chapters: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {}
  },
  computed: {
    show: {
      get() {
        return this.value
      },
      set(val) {
        this.$emit('input', val)
      }
    }
  },
  methods: {
    clickedOption(chapter) {
      this.$emit('select', chapter)
    }
  },
  mounted() {}
}
</script>