<template>
    <button class="top-right-button" @click="$emit('switchToHome')">
      Home
    </button>
    <div class="p-5 text-center home">
        <h1 class="mb-5 text-3xl font-bold">Liked Cat Gallery</h1>
        <div class="grid grid-cols-1 gap-4 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
            <div
                v-for="(cat, index) in this.likedImages.slice(0, 8)"
                :key="index"
                class="overflow-hidden rounded-lg shadow-lg cursor-pointer"
                @click="openModal(cat)"
            >
                <img :src="cat" alt="Cute Cat" class="object-cover w-full h-full" />
            </div>
        </div>

        <!-- Modal -->
        <div v-if="showModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50">
            <div class="relative bg-white rounded-lg shadow-lg">
                <button
                    class="absolute text-gray-500 top-2 right-2 hover:text-gray-800"
                    @click="closeModal"
                >
                    ✖
                </button>  

                <button
                    class="absolute text-gray-500 left-2 top-2 hover:text-gray-800"
                    @click="like"
                >
                    <div v-if="isLiked">❤️</div>
                    <div v-if="!isLiked">❤️</div >
                </button>

                <img :src="selectedImage" alt="Large Cat" class="max-w-full max-h-screen rounded-lg" />
            </div>
        </div>
    </div>
</template>

<script>
import { stringify } from 'postcss';

export default {
    data() {
        return {
            showModal: false,
            selectedImage: null,
            isLiked: false,
            likedImages: [],
        };
    },
    async created() {

        this.likedImages = JSON.parse(localStorage.getItem("liked"));
        if(!this.likedImages){
            this.likedImages = [];
        }


    },
    methods: {
        openModal(imageUrl) {
            this.selectedImage = imageUrl;
            this.showModal = true;
        },
        closeModal() {
            this.showModal = false;
            this.selectedImage = null;
        },
        like() {

            const index = this.likedImages.indexOf(this.selectedImage);
            if (index > -1) {
                this.likedImages.splice(index, 1);
            }
            

            localStorage.setItem("liked", JSON.stringify(this.likedImages));

            this.closeModal();
        },
    },
};
</script>

<style scoped>

.top-right-button {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
}
img {
    object-fit: cover;
}

.fixed {
    position: fixed;
}

.inset-0 {
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}

.z-50 {
    z-index: 50;
}


.cursor-pointer {
    cursor: pointer;
}
</style>
