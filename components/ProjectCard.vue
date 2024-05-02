<template>
    <div id="project" :key="key" class="lg:mx-5">

        <span class="flex text-sm my-3">
            <h3 v-if="index == null" class="text-purplefy font-fira_bold mr-3">Project {{ key + 1 }}</h3>
            <h3 v-else class="text-purplefy font-fira_bold mr-3">Project {{ index + 1 }}</h3>
            <h4 class="font-fira_retina text-menu-text"> // {{ project.title }}</h4>
        </span>

        <div id="project-card" class="flex flex-col">
            <div id="window">
                <img id="showcase" :src="project.img" :alt="project.title" class="">
            </div>

            <div class="pb-8 pt-6 px-6 border-top">
                <p class="text-menu-text font-fira_retina text-sm mb-5">
                {{ project.description }}
                </p>
                   <a id="view-button" :href="project.url" target="_blank" class="text-white font-fira_retina py-2 px-4 w-fit text-xs rounded-lg mr-3">
                    view-project
                   </a>
                   <button id="view-button" @click="openDialog" class="text-white font-fira_retina py-2 px-4 w-fit text-xs rounded-lg">
                    video-demo
                   </button>
              <div v-show="isOpen">
                <div class="mt-3">
            <iframe :v-if="project.video!=''" width="360" height="315" :src="project.video" frameborder="0" allowfullscreen></iframe>
            <button @click="closeDialog" class="text-white font-fira_retina py-2 px-4 w-fit text-xs rounded-lg">Close</button>
          </div>
              </div>     
  
            </div>
        </div>
    </div>
</template>

<script setup>
const { project, key, index } = defineProps(['project', 'key', 'index'])
const isOpen=ref(false);
 function openDialog() {
      isOpen.value = true;
    }
   function closeDialog() {
      isOpen.value = false;
    }
</script>

<style scoped>
#project {
  min-width: 400px;
  margin-bottom: 5px;
}

#project-card {
  border: 1px solid #1E2D3D;
  background-color: #011221;
  border-radius: 15px;
  max-width: 400px;
}

#window {
  max-height: 160px;
  position: relative;
  overflow: hidden;
}

#showcase {
  border-top-right-radius: 15px;
  border-top-left-radius: 15px;
}

@media (max-width: 768px) {
  #project {
    min-width: 100%;
  }
}

@media (min-width: 768px) {
  #project {
    width: 100%;
    min-width: 100%;
    padding-inline: 5px;
  }
}

@media (min-width: 1350px) {
  #project {
    width: 100%;
    min-width: 100%;
    padding-inline: 20px;
  }
}

</style>