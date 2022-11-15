<template>
  <div class="px-4 flex flex-col gap-3">
    <h3>Tulis kisah mleyotmu :(</h3>
    <textarea v-model="post" rows="10" class="
      bg-gray-100 
      border-gray-500 
      w-full pt-2 pl-3
      rounded-md
      outline
      border-none focus:ring-0
      focus:ring-blue-300
    "></textarea>
    
    <div class="flex justify-end pt-1">
      <div class="bg-blue-400 border-gray-500 rounded-lg px-2 py-3 text-white font-bold cursor-pointer" @click="addPost">
        mleyot
      </div>
    </div>

    <div v-for="(post, i) in posts" class="rounded-md relative">
        <img src="https://picsum.photos/600/600" alt="" @dblclick="addLikes(i)">
        
        <span class="text-center text-3xl text-white absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
        {{post.content}}
        </span>
        <div @click="addLikes(i)" class="z-10">
            ❤️ {{post.likes}}
        </div>
    </div>
  </div>
</template>

<script>
export default {
    data(){
      return {
        post: '',
        posts: [],
      };
    },
    methods: {
      addPost() {
        this.posts.push({
          content: this.post,
          likes: 0,
        });
        this.post = '';
      },

      addLikes(index) {
        this.posts[index].likes++;
      },
    },
}
</script>
