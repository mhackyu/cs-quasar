<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md" style="max-width: 400px">
      <h2>Music Library</h2>
      <form @submit.prevent="handleSubmit">
        <q-input outlined autofocus v-model="title" label="Title" />
        <q-input outlined v-model="artist" label="Artist" />
        <q-btn
          type="submit"
          class="full-width q-mt-md"
          :color="isEdit ? 'positive' : 'primary'"
          :label="isEdit ? 'Update' : 'Submit'"
        />
      </form>
      <q-list bordered separator class="q-mt-md">
        <q-item v-if="musics.length === 0">
          <q-item-section>
            <q-item-label class="text-center">
              Library is empty.
              </q-item-label>
          </q-item-section>
        </q-item>
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
              @click="confitmDelete(index)"
            >
              <q-icon name="delete" />
            </q-btn>
          </q-item-section>
        </q-item>
      </q-list>
    </div>
    <q-dialog v-model="isDelete" persistent>
      <q-card>
        <q-card-section class="row items-center">
          <q-avatar icon="help" color="negative" text-color="white" />
          <span class="q-ml-sm"
            >Are you sure you want to delete this item?</span
          >
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Cancel" color="primary" v-close-popup />
          <q-btn
            flat
            label="Yes, I want to delete"
            color="primary"
            @click="deleteItem(selectedIndex)"
          />
        </q-card-actions>
      </q-card>
    </q-dialog>
    <q-dialog v-model="showPlayer" position="bottom">
      <q-card style="width: 350px">
        <q-linear-progress :value="0.1" color="pink" />

        <q-card-section class="row items-center no-wrap">
          <div>
            <div class="text-weight-bold">{{selectedMusic.title}}</div>
            <div class="text-grey">{{selectedMusic.artist}}</div>
          </div>

          <q-space />

          <q-btn flat round icon="fast_rewind" />
          <q-btn flat round icon="pause" />
          <q-btn flat round icon="fast_forward" />
        </q-card-section>
      </q-card>
    </q-dialog>
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
      selectedIndex: null,
      isDelete: false,
      showPlayer: false,
      selectedMusic: {}
    };
  },
  methods: {
    handleSubmit() {
      if (!this.isEdit) {
        // Add new music
        this.musics.push({
          title: this.title,
          artist: this.artist
        });
      } else {
        // Update current selected music
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
    confitmDelete(index) {
      this.isDelete = true;
    },
    deleteItem(index) {
      this.musics.splice(index, 1);
      this.selectedIndex = null;
      this.isDelete = false;
    },
    playMusic(music) {
      this.selectedMusic = music;
      this.showPlayer = true;
    }
  }
};
</script>
