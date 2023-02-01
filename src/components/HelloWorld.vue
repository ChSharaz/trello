<template>
  <div
    class="main-section"
    :style="{ background: color, backgroundImage: `url(${imageUrl})` }"
  >
    <div>
      <b-navbar
        toggleable="lg"
        type="dark"
        :style="{ background: color, backgroundImage: `url(${imageUrl})` }"
      >
        <b-navbar-brand href="#">Trello</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item-dropdown text="Workspaces">
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Vue">
              <b-dropdown-item href="#">Tasks</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Starred">
              <b-dropdown-item href="#"
                >Star important boards to access them quickly and
                easily.</b-dropdown-item
              >
            </b-nav-item-dropdown>
            <b-nav-item-dropdown text="Tamplates">
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>

          <b-navbar-nav class="ml-auto">
            <div class="search-section">
              <b-icon icon="search"></b-icon>

              <input
                type="text"
                class="input-text-section"
                placeholder="Search"
              />
            </div>

            <div class="icons d-flex align-items-center">
              <b-icon class="mr-2 ml-2 icon1" icon="bell"></b-icon>
              <b-icon class="mr-2 icon1" icon="question-circle"></b-icon>
              <b-icon class="mr-2 icon2" icon="person-circle"></b-icon>
            </div>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <div class="after-nav-section">
      <div
        class="section-one d-flex justify-content-between align-items-center mx-3"
      >
        <div class="first d-flex justify-content-between align-items-center">
          <div class="title icons d-flex align-baseline mr-2">
            <h6>Usama Task</h6>
            <b-icon class="mr-2 ml-2 icon1" icon="star"></b-icon>
          </div>
          <div class="filter icons icon3 d-flex align-baseline mr-2">
            <b-icon class="mr-2 ml-2 icon1" icon="people"></b-icon>
            <h6>Workspaces Visivle</h6>
          </div>
          <div class="board-h icons icon3 d-flex align-baseline">
            <b-icon class="mr-2 ml-2 icon1" icon="option"></b-icon>
            <h6>Board</h6>
          </div>
        </div>
        <div class="second d-flex justify-content-between align-items-center">
          <div class="powerup-automation d-flex mx-2">
            <div class="filter icons icon3 d-flex align-baseline mr-2">
              <b-icon class="mr-2 ml-2 icon1" icon="cursor"></b-icon>
              <h6>Power-Ups Task</h6>
            </div>
            <div class="filter icons icon3 d-flex align-baseline mr-2">
              <b-icon class="mr-2 ml-2 icon1" icon="lightning"></b-icon>
              <h6>Automation</h6>
            </div>
          </div>

          <div class="filter icons icon3 d-flex align-baseline mr-2">
            <b-icon class="mr-2 ml-2 icon1" icon="filter"></b-icon>
            <h6>Filter</h6>
          </div>
          <div class="icons icon2">
            <b-icon class="mr-2 icon2" icon="person-circle"></b-icon>
          </div>
          <div class="btn">
            <b-button variant="light">Share</b-button>
          </div>
          <div class="icons icon3">
            <b-icon
              v-b-toggle.sidebar-right
              class="mr-2 icon2"
              icon="three-dots"
            ></b-icon>

            <b-sidebar id="sidebar-right" title="Menu" right shadow>
              <div>
                <div class="mb-3">
                  <b-button v-b-toggle.my-collapse
                    >Change Background-Color</b-button
                  >
                </div>

                <b-collapse id="my-collapse">
                  <b-card>
                    <div class="theme-options">
                      <div class="own-color">
                        <h5>Set Your Own Color</h5>
                        <input v-model="color" type="color" />
                        <b-button
                          @click="addclrList"
                          class="clr-btn mt-2 btn-block"
                          variant="danger "
                          >Add a List</b-button
                        >
                      </div>
                      <div class="default mt-4">
                        <h5>By Default</h5>
                        <div class="background-theme">
                          <div
                            class=""
                            v-for="(theme, index) in backgroundthemes"
                            :key="index"
                            @click="swicthTheme(theme)"
                          >
                            <div
                              class="clrs"
                              :style="{ background: theme }"
                            ></div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </b-card>
                </b-collapse>
              </div>
              <div>
                <b-button v-b-toggle.collapse-3 class="m-1"
                  >Change Background Img</b-button
                >
                <b-collapse visible id="collapse-3">
                  <b-card>
                    <input
                      type="file"
                      accept="image/*"
                      @change="onChange"
                      class="upload-img"
                    />
                    <div id="preview" class="py-2">
                      <img
                        class="w-50"
                        v-if="item.imageUrl"
                        :src="item.imageUrl"
                      />
                      <b-button
                        @click="addbgList"
                        class="clr-btn mt-2 btn-block"
                        variant="danger "
                        >Add a List</b-button
                      >
                    </div>
                    <div class="default mt-4">
                      <h5>By Default</h5>
                      <div class="background-theme">
                        <div
                          class="text-h2"
                          v-for="(images, index) in imgs"
                          :key="index"
                        >
                          <img :src="images.bgimg" @click="nextImage(index)" />
                          <!-- <img :src="images" @click="nextImage" /> -->
                        </div>
                      </div>
                    </div>
                  </b-card>
                </b-collapse>
              </div>
            </b-sidebar>
          </div>
        </div>
      </div>

      <div class="todo-section">
        <div class="form-section d-flex align-baseline board">
          <b-form-input
            type="text"
            @keyup.ctrl.enter="addList"
            v-model="name"
            placeholder="+ Add a list"
          ></b-form-input>

          <div v-if="btnEnable" class="other-btn d-flex align-baseline">
            <b-button
              class="mx-2"
              @click="updateTask"
              @keyup.ctrl.enter="updateTask"
              :disabled="name.trim() === ''"
              variant="outline-dark"
              >Update</b-button
            >
          </div>
          <div v-else class="add">
            <b-button
              class="mx-2"
              @click="addList"
              :disabled="name.trim() === ''"
              variant="outline-dark"
              >Add</b-button
            >
          </div>
        </div>
        <div class="todo-section2 py-2 d-flex align-items-start">
          <div
            class="tasks-icons d-flex justify-content-between board p-3 my-2 mr-2"
            v-for="(detail, index) in details"
            :key="index"
          >
            <div class="taskCardWrapper">
              <div
                class="first d-flex align-items-baseline justify-content-between gap-2 w-100"
              >
                <h6
                  :class="{ 'textunderline text-danger': detail.Validate }"
                  class="mb-3"
                >
                  {{ index + 1 }} {{ detail.title }}
                </h6>
                <div class="icons d-flex align-baseline">
                  <div @click="pop(index)" class="trash mx-2">
                    <b-icon variant="danger" icon="trash"></b-icon>
                  </div>
                  <div @click="editTask(index)" class="edit">
                    <b-icon variant="primary" icon="pencil-square"></b-icon>
                  </div>
                </div>
              </div>
              <div
                class="sub-input d-flex justify-content-between align-items-center"
              >
                <b-form-input
                  type="text"
                  @keyup.ctrl.enter="addList"
                  placeholder="+ Add a card"
                  v-model="detail.subtaskTitle"
                ></b-form-input>
                <div v-if="detail.btnsubEnable === false" class="updatesubtask">
                  <b-button
                    class="mx-2"
                    :disabled="detail.subtaskTitle.trim() === ''"
                    @click="addsubList(index)"
                    variant="outline-dark"
                    >Add</b-button
                  >
                </div>
                <div v-else class="addsubtask">
                  <b-button
                    class="mx-2"
                    @click="updatesubTask(index)"
                    variant="outline-dark"
                    >Update</b-button
                  >
                </div>
              </div>
              <div
                v-for="(subTask, i) in detail.list"
                :key="i"
                class="border px-2 my-2 py-2 w-100 mb-2"
              >
                <div
                  class="subinput-icons d-flex justify-content-between align-items-center"
                >
                  <div class="div">
                    {{ subTask }}
                  </div>
                  <div class="icons d-flex align-baseline">
                    <!-- <div class="edit">
                      <b-icon variant="primary" icon="cursor-fill"></b-icon>
                    </div> -->
                    <div class="trash mx-2" @click="subtaskDlt(index, i)">
                      <b-icon variant="danger" icon="trash"></b-icon>
                    </div>
                    <div @click="editsubTask(index, i)" class="edit">
                      <b-icon variant="primary" icon="pencil-square"></b-icon>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "imageUpload",

  data() {
    return {
      name: "",
      color: "",
      btnEnable: false,
      editedTask: null,
      editedsubTask: null,
      currentImageIndex: 0,
      details: [
        {
          title: "Topics/Concepts to Revise",
          list: ["HTML Elements", "HTML Form Validation"],
          subtaskTitle: "",
          btnsubEnable: false,
        },
        {
          title: "Task To Do",
          list: [
            "Read new CSS-Tricks articles",
            "Begin draft of CSS Grid article",
            "Begin draft of CSS Grid article",
          ],
          subtaskTitle: "",
          btnsubEnable: false,
        },
      ],
      backgroundthemes: ["#000000", "#42A98F", "#297afb", "#2898fb", "#01d8fd"],
      imgs: [
        {
          bgimg: require("@/assets/1.png"),
        },
        {
          bgimg: require("@/assets/2.png"),
        },
        {
          bgimg: require("@/assets/3.png"),
        },
        {
          bgimg: require("@/assets/6.png"),
        },
        {
          bgimg: require("@/assets/7.png"),
        },
        {
          bgimg: require("@/assets/8.png"),
        },
        // require("@/assets/1.png"),
        // require("@/assets/2.png"),
        // require("@/assets/3.png"),
        // require("@/assets/6.png"),
        // require("@/assets/7.png"),
        // require("@/assets/8.png"),
      ],
      item: {
        image: null,
        imageUrl: null,
      },
    };
  },
  computed: {
    imageUrl() {
      return this.imgs[this.currentImageIndex].bgimg;
    },
  },
  methods: {
    nextImage(inex) {
      this.currentImageIndex = inex;
    },
    addbgList() {
      this.imgs.push({ bgimg: this.item.imageUrl });
    },
    swicthTheme(theme) {
      this.color = theme;
    },
    addclrList() {
      this.backgroundthemes.push(this.color);
    },
    onChange(e) {
      const file = e.target.files[0];
      this.image = file;
      this.item.imageUrl = URL.createObjectURL(file);
    },
    addList() {
      this.details.push({
        title: this.name,
        list: [],
        subtaskTitle: "",
        btnsubEnable: false,
      });
      this.name = "";
    },
    pop(index) {
      this.details.splice(index, 1);
    },
    editTask(index) {
      this.name = this.details[index].title;
      this.btnEnable = true;
      this.editedTask = index;
    },

    updateTask() {
      if (this.editedTask === null) {
        this.name = "";
      } else {
        this.details[this.editedTask].title = this.name;
        this.editedTask = null;
        this.btnEnable = false;
        this.name = "";
      }
    },

    addsubList(index) {
      this.details[index].list.push(this.details[index].subtaskTitle);
      this.details[index].subtaskTitle = "";
    },

    subtaskDlt(index, i) {
      this.details[index].list.splice(i, 1);
    },

    editsubTask(index, i) {
      this.details[index].subtaskTitle = this.details[index].list[i];
      this.details[index].btnsubEnable = true;
      this.editedsubTask = i;
    },

    updatesubTask(index) {
      if (this.editedsubTask === null) {
        this.details[index].subtaskTitle = "";
        this.details[index].btnsubEnable = false;
      } else {
        this.details[index].list[this.editedsubTask] =
          this.details[index].subtaskTitle;
        this.editedsubTask = null;
        this.details[index].subtaskTitle = "";
        this.details[index].btnsubEnable = false;
      }
    },
  },
};
</script>

<style scoped>
.main-section {
  background-repeat: no-repeat !important;
  background-size: cover !important;
  background-color: rgba(0, 0, 0, 0.3490196078);
}
nav.navbar {
  background-repeat: no-repeat !important;
  background-size: cover !important;
  background-color: rgba(0, 0, 0, 0.3490196078);
}
.clrs {
  cursor: pointer;
  width: 50px;
  height: 50px;
  border-radius: 4px;
  margin: 4px 10px;
  border: 1px solid white;
  display: inline-block;
}
.theme-options {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}
.text-h2 img {
  cursor: pointer;
  width: 70px;
  height: 60px;
  border-radius: 4px;
  margin: 4px px 10px;
  border: 1px solid white;
}
.colors {
  cursor: pointer;
  width: 50px;
  height: 50px;
  border-radius: 4px;
  margin: 4px 10px;
  border: 1px solid white;
  display: inline-block;
}
.colors.active {
  box-shadow: 0 0 3px 5px #1e1c1c2b;
  border: 1px solid #1e1c1c12;
}

.search-section {
  padding: 3px 7px;
  border-radius: 10px;
  border: 1px solid #ffffff75;
}
.input-text-section {
  background-color: transparent;
  color: white !important;
  border: none !important;
}
input:focus-visible {
  border: none;
}
nav {
  border-bottom: 1px solid #ffffffcf;
}
.board-h {
  background: white;
  color: black;
  padding: 5px;
  border-radius: 5px;
}
.board {
  background: white;
  color: black;
  padding: 5px;
  border-radius: 5px;
  width: 300px;
}
.title {
  border-right: 1px solid #ffffff6b;
}
.powerup-automation {
  border-right: 1px solid #ffffff6b;
}
.filter {
  background: #ffffff2b;
  border-radius: 5px;
  padding: 5px 10px;
}
h6 {
  margin: 0;
  font-weight: 600;
}
h5 {
  text-align: left;
  color: black;
  font-size: 16px;
  font-weight: 600;
}
svg.bi-search.b-icon.bi {
  color: white;
}
.todo-section {
  padding: 30px;
}
button.btn.add-btn.btn-secondary {
  background: #37b7cb;
  border: #37b7cb;
}
</style>
<style>
span {
  color: white;
}
.icons {
  color: white;
  cursor: pointer;
}
.upload-img {
  font-size: 15px;
}
.main-section {
  background-color: #454145;
}
.icons .icon1 {
  cursor: pointer;
  font-size: 20px;
}
.icons .icon1:hover {
  color: #f2d600;
}
.icons .icon2 {
  font-size: 25px;
}
.icons .icon3 {
  cursor: pointer;
  font-size: 20px;
}

.taskCardWrapper {
  width: 300px;
}

.todo-section {
  width: 100%;
  max-width: 100%;
  overflow-x: auto;
  height: calc(100vh - 110px);
}
button.btn.btn-secondary.collapsed {
  margin: 10px 45px !important;
  background-color: black;
}
button.btn.btn-secondary.not-collapsed {
  margin: 10px 45px !important;
  background-color: black;
}
.b-sidebar.b-sidebar-right > .b-sidebar-header .close {
  margin-right: 80px !important;
}
header.b-sidebar-header {
  background: black;
  color: white;
}
svg.bi-x.b-icon.bi {
  color: white;
}
input[type="color"] {
  width: 255px;
  height: 120px;
}
.clr-btn {
  text-align: center;
}
.background-theme {
  display: grid;
  grid-template: 70px / auto auto auto;
  padding: 10px;
}
</style>
