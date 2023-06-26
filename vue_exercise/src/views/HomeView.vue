<template>
  <h1>People</h1>
  <div id="disp"></div>
  <Footer/>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'


// export default {
//   name: 'HomeView',
//   components: {
//     HelloWorld
//   }
// }

import Footer from '@/components/footer.vue';

export default {
   components: {
    Footer
   }
  }

  async function getStudents(){
      const data = await fetch('https://lithiniskhikhi.github.io/json-server-url/user.JSON')
      const formatData = await data.json()
      let fetchedData = formatData.people
      const display = document.querySelector('#disp')
      fetchedData.forEach(people =>{
      display.innerHTML += `
      <div class="card">
          <div class="card-body">
            <h3 class="card-title">${people.firstName}</h3>
            <p class="card-text">${people.lastName}</p>
            <p class="card-text">${people.age}</p>
          </div>
        </div>
    `
  })
  }
  getStudents()

</script>
