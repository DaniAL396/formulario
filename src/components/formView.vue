<template>
  <form @submit.prevent="handleSubmit" class="form">
    <h2>Formulario de Registro</h2>

    <div>
      <label for="name">Nombre</label>
      <input id="name" v-model.trim="form.name" required />
    </div>

    <div>
      <label for="address">Dirección</label>
      <input id="address" v-model.trim="form.address" required />
    </div>

    <div>
      <label for="age">Edad</label>
      <input id="age" type="number" v-model.number="form.age" min="1" required />
    </div>

    <button type="submit">Enviar</button>
  </form>
</template>

<script setup>
import { reactive } from 'vue'

const form = reactive({
  name: '',
  address: '',
  age: null,
})

function handleSubmit() {
  // Validaciones simples
  if (!form.name || !form.address || !form.age) {
    alert('Por favor completa todos los campos.')
    return
  }

  console.log('Formulario enviado:', { ...form })
  alert('Formulario enviado (revisa la consola).')

  // Limpiar formulario
  form.name = ''
  form.address = ''
  form.age = null
}
</script>

<style scoped>
.form { 
  max-width:480px; 
  margin:16px auto; 
  padding:12px; 
  border:1px solid #e0e0e0; 
  border-radius:8px; 
}
.form > div { margin-bottom:10px; }
h2 { text-align:center; margin-bottom:12px; }
label { display:block; font-weight:600; margin-bottom:4px; }
input { width:100%; padding:8px; border:1px solid #ccc; border-radius:6px; }
button { padding:8px 12px; border-radius:6px; cursor:pointer; display:block; margin-top:10px; }
</style>
