<template>
    <div  class="rs-drop-down  select-none w-full text-sm ">
        <button :class="classButton" :color="color" class="m-0 flex items-center gap-3 p-3 rounded-lg"
                @click="menuVisibility = !menuVisibility">
          <img src="~/assets/svg/Menu.svg">

          <span class="flex items-center flex-grow">
              <span v-if="text === ''" class="text-sm font-light text-gray-400">Select</span>
                <span v-else
                      class="whitespace-nowrap px-0">
                    {{ text }}
                </span>
            </span>

        </button>
        <div  v-if="menuVisibility" class="rs-drop-down--list-parent relative ">
            <ul :class="classList" :style="styleList"
                class="absolute left-0 right-0 top-1 z-50 bg-white shadow-xl rounded-lg flex flex-col gap-2 p-3 text-sm transition-all transform">
                <li v-for="item in source" :class="{'selected' : selected === item }" @click="updateModel(item)" class="cursor-pointer hover:text-secondary">
                    {{ item }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>

export default {
        name: 'DropDown',

        model: {
            prop: 'selected',
            event: 'change',
        },

        props: {
            classButton: {},
            classList: {},
            styleList: {},
            color: {
                default: '',
                type: String,
                required: false,
            },
            name: {
                default: '',
                type: String,
                required: false,
            },
            placeholder: {
                default: '',
                type: String,
                required: false,
            },
            rules: {
                default: null,
            },
            selected: {
                default: '',
                type: String,
                required: false,
            },
            source: {
                default: () => ([]),
                type: Array,
                required: false,
            },
        },

        data() {
            return {
                menuVisibility: false,
            }
        },

        computed: {
            model: {
                get() {
                    return this.selected
                },
                set(selected) {
                    this.$emit('change', selected)
                },
            },
            text() {
                return this.selected
            },
        },

        methods: {
            hideMenu() {
                this.menuVisibility = false
            },
            updateModel(key) {
                this.menuVisibility = false
                this.selected = key
            },
        },
    }
</script>

<style>
.rs-drop-down {
    color: #000;
}
.rs-drop-down button {
    width: 100%;
    position: relative;
    box-sizing: border-box;
    line-height: 18px;
    cursor: pointer;
}
.ltr .rs-drop-down button span:nth-child(1) {
    padding-right: 20px;
}
.rtl .rs-drop-down button span:nth-child(1) {
    padding-left: 20px;
}
.rs-drop-down.small button {
    padding: 4px 8px;
}
.rs-drop-down.small button span {
    font-size: 0.75rem;
}
.ltr .rs-drop-down.small button span:nth-child(1) {
    padding-right: 16px;
}
.rtl .rs-drop-down.small button span:nth-child(1) {
    padding-left: 16px;
}
.rs-drop-down.x-small button {
    padding: 3px 6px;
}
.rs-drop-down.x-small button span {
    font-size: 0.75rem;
}
.ltr .rs-drop-down.x-small button span:nth-child(1) {
    padding-right: 12px;
}
.rtl .rs-drop-down.x-small button span:nth-child(1) {
    padding-left: 12px;
}
.rs-drop-down.xx-small button {
    padding: 2px 4px;
}
.rs-drop-down.xx-small button span {
    font-size: 0.75rem;
}
.ltr .rs-drop-down.xx-small button span:nth-child(1) {
    padding-right: 8px;
}
.rtl .rs-drop-down.xx-small button span:nth-child(1) {
    padding-left: 8px;
}
.rs-drop-down.xx-small .rs-drop-down--list-parent ul {
    left: 0;
    right: 0;
    background-color: #ffffff;
    z-index: 10;
}
.rs-drop-down.xx-small .rs-drop-down--list-parent ul li {
    padding: 2px 4px;
    font-size: 0.75rem;
    font-weight: 100;
    cursor: pointer;
}
.rs-drop-down.xx-small .rs-drop-down--list-parent ul li:hover {
    background-color: #1e88e5;
}

</style>
