<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md" style="max-width: 400px">
      <h2>Music Library</h2>
      <form @submit.prevent="handleSubmit">
        <q-input outlined autofocus v-model="title" label="Title" />
        <q-input outlined v-model="artist" label="Artist" />
        <q-btn
          type="submit"
          class="full-width"
          :color="isEdit ? 'positive' : 'primary'"
          :label="isEdit ? 'Update' : 'Submit'"
        />
      </form>
      <q-list bordered separator>
        <q-item
          clickable
          v-ripple
          v-for="(music, index) in musics"
          :key="index"
        >
          <q-item-section>
            <q-item-label>{{ music.title }}</q-item-label>
            <q-item-label caption>{{ music.artist }}</q-item-label>
          </q-item-section>
          <q-item-section right>
            <q-btn
              class="full-width"
              color="positive"
              @click="editItem(music, index)"
            >
              <q-icon name="edit" />
            </q-btn>
            <q-btn
              class="full-width"
              color="negative"
              @click="deleteItem(index)"
            >
              <q-icon name="delete" />
            </q-btn>
          </q-item-section>
        </q-item>
      </q-list>
    </div>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      musics: [
        {
          title: "Bida Ang Saya",
          artist: "Jollibee"
        },
        {
          title: "Love Ko 'To",
          artist: "MC Donald"
        }
      ],
      title: "",
      artist: "",
      isEdit: false,
      selectedIndex: null
    };
  },
  methods: {
    handleSubmit() {
      if (!this.isEdit) {
        this.musics.push({
          title: this.title,
          artist: this.artist
        });
      } else {
        this.musics[this.selectedIndex] = {
          title: this.title,
          artist: this.artist
        };
        this.isEdit = false;
        this.selectedIndex = null;
      }
      this.title = "";
      this.artist = "";
    },
    editItem(music, index) {
      console.log("info ", { music, index });
      this.title = music.title;
      this.artist = music.artist;
      this.isEdit = true;
      this.selectedIndex = index;
    },
    deleteItem(index) {
      this.musics.splice(index, 1);
    }
  }
};
</script>
