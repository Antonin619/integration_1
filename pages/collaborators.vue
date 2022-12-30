<template>
    <div class="collaborators p-8">
        <div class="collaborators-header">
            <h1>Collaborators</h1>
            <a href="#form"><button  class="add-collaborator-button">Add +</button></a>
        </div>

        <Collaborator v-for="collaborator in collaborators" :key="collaborator.id" :id="collaborator.id" :picture="collaborator.picture  || null" :firstname="collaborator.firstname" :lastname="collaborator.lastname" :role="collaborator.role" :description="collaborator.description || null" :portfolio="collaborator.portfolio || null"/>
    
        <h2>Add new Collaborators</h2>
        <h5>New members ? Add them here !</h5>

        <form
        id="form"
        @submit="checkForm"
        action=""
        method="post"
        >

        <p class="mt-4" v-if="errors.length">
            <b>* Required fields.</b>
            <ul style="color: red; font-size: 12px;">
            <li v-for="error in errors">{{ error }}</li>
            </ul>
        </p>
        
        <div class="form-inputs">
            <label for="firstname">Firstname*</label>
            <input
            id="firstname"
            v-model="formFirstname"
            type="text"
            name="firstname"
            >
        

        
            <label for="lastname">Lastname*</label>
            <input
            id="lastname"
            v-model="formLastname"
            type="text"
            name="lastname"
            >
        

        
            <label for="role">Role*</label>
            <input
            id="role"
            v-model="formRole"
            type="text"
            name="role"
            >
        

        
            <label for="description">Description</label>
            <textarea
            id="description"
            v-model="formDescription"
            type="text"
            name="description"
            ></textarea>
        

        
            <label for="portfolio">Portfolio</label>
            <input
            id="portfolio"
            v-model="formPortfolio"
            type="text"
            name="portfolio"
            placeholder="https://"
            >
        
        
        
            <input
            type="submit"
            value="Add"
            class="submit-button"
            >
        
            
        </div>
        </form>
    </div>
</template>

<script lang="ts" setup>

const formFirstname = ref('')
const formLastname = ref('')
const formRole = ref('')
const formDescription = ref('')
const formPortfolio = ref('')
const errors = ref([''])

const collaborators = ref([
    {
        id: 1,
        picture:"./_nuxt/assets/user1.jpg",
        firstname:"John",
        lastname:"Doe",
        role:"Designer",
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nunc ut aliquam tincidunt, nunc nisl aliquam nisl, eu aliquam nisl nisl sit amet lorem. Sed euismod, nunc ut aliquam tincidunt, nunc nisl aliquam nisl, eu aliquam nisl nisl sit amet lorem.",
        portfolio:"https://www.google.com"
    },
    {
        id: 2,
        picture:"./_nuxt/assets/user2.jpg",
        firstname:"Jan",
        lastname:"Kowalski",
        role:"Developper",
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit"
    },
    {
        id: 3,
        picture:"./_nuxt/assets/user3.jpg",
        firstname:"Anita",
        lastname:"Einstein",
        role:"Content Creator",
        portfolio:"https://www.google.com"
    },
    {
        id: 4,
        firstname:"Etienne",
        lastname:"Dupont",
        role:"Project Manager",
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nunc ut aliquam tincidunt, nunc nisl aliquam nisl, eu aliquam nisl nisl sit amet lorem. Sed euismod, nunc ut aliquam tincidunt, nunc nisl aliquam nisl, eu aliquam nisl nisl sit amet lorem.",
    },
    {
        id: 5,
        picture:"./_nuxt/assets/user4.jpg",
        firstname:"Zoe",
        lastname:"Parker",
        role:"Editor",
    },
])



function checkForm(e:any) {
      

      errors.value = [''];

      if (!formFirstname.value) {
        errors.value.push('First name is required.');
      }
      if (!formLastname.value) {
        errors.value.push('Last name is required.');
      }
      if (!formRole.value) {
        errors.value.push('Role is required.');
      }

      e.preventDefault();

      if (formFirstname.value && formLastname.value && formRole.value) {
        collaborators.value.push({
        id: collaborators.value.length + 1,
        picture: '',
        firstname: formFirstname.value,
        lastname: formLastname.value,
        role: formRole.value,
        description: formDescription.value,
        portfolio: formPortfolio.value
      })
      }
      
    }

</script>

<style lang="scss" scoped>
.collaborators-header {
    display: flex;
    align-items: center;
    margin-bottom: 2rem;
    gap: 1rem;

    h1 {
        margin: 0;
    }

    .add-collaborator-button {
        background-color: rgb(71, 0, 185);
        color: rgb(255, 255, 255);
        border: none;
        border-radius: 0.5rem;
        padding: 0.5rem 1rem;
        font-size: 12px;
        cursor: pointer;
        font-weight: 600;
    }
}



.form-inputs {

    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: center;

    label {
        margin-top: 0.5rem;
    }

    input {
        
        height: 2rem;
        background-color: rgb(255, 255, 255);
        border: 1px solid rgb(71, 0, 185);
        padding-left: 0.5rem;
        border-radius: 0.5rem;
    }

    textarea {
        min-height: 5rem;
        background-color: rgb(255, 255, 255);
        border: 1px solid rgb(71, 0, 185);
        resize: none;
        border-radius: 0.5rem;
    }

    .submit-button {
        background-color: rgb(71, 0, 185);;
        margin-top: 2rem;
        color: white;
        font-weight: 600;
        padding: 0.5rem 0rem 0.5rem 0rem;
        height: auto; 
        border-radius: 0.5rem;       
    }
}

</style>