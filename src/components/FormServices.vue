<template>
  <div class="form-services">
    <form class="vue-form" >

      <div class="error-message">
        <p v-show="!email">Oh, please enter a valid email address.</p>
      </div>

      <fieldset>
        <legend>Vue Contact Form</legend>
        <div>
          <label class="label" for="name">Nombre</label>
          <input type="text" name="name" id="name" required v-model="name">
        </div>
        <div>
          <label class="label" for="email">Email</label>
          <input type="email" name="email" id="email" v-model="email">
        </div>
        <div>
          <label class="label" for="phone">Teléfono</label>
          <input type="phone" name="phone" id="phone" v-model="phone">
        </div>
        <div>
          <label class="label" for="time">Horario de preferencia</label>
          <select name="time" id="time" v-model="time">
            <option value="09:00 - 10:00">09:00 - 10:00</option>
            <option value="10:00 - 11:00">10:00 - 11:00</option>
            <option value="11:00 - 12:00">11:00 - 12:00</option>
            <option value="12:00 - 13:00">12:00 - 13:00</option>
            <option value="13:00 - 14:00">13:00 - 14:00</option>
          </select>
        </div>
        <div>
          <label class="label" for="service">Horario de preferencia</label>
          <select name="service" id="service" v-model="service">
            <option value="desarrollo-web">Desarrollo web</option>
            <option value="desarrollo-tienda-online">Desarrollo tienda online</option>
            <option value="aplicacion-movil">Aplicación móvil</option>
            <option value="posicionamiento-rrss">Posicionamiento en redes sociales</option>
            <option value="hosting-dominios">Hosting y dominios</option>
            <option value="diseño-grafico">Diseño gráfico</option>
            <option value="marketing-360">Marketing 360</option>
            <option value="asesoria">Asesoría</option>
          </select>
        </div>
        <div>
          <label class="label" for="description">Descripción</label>
          <textarea name="description" id="description" v-model="description"></textarea>
        </div>

        <div>
          <input type="button" value="Enviar" @click="handleBtn">
        </div>
      </fieldset>
    </form>

    <teleport to="#modal-form-ok">
      <modal :show="showModal" @close="showModal = false">
        <h2>Ha pedido nuestro servicio con los siguientes datos:</h2>
        <p>{{name}}</p>
        <p>{{email}}</p>
        <p>{{phone}}</p>
        <p>{{time}}</p>
        <p>{{service}}</p>
        <p>{{description}}</p>
        <h2>En breve contactaremos con usted. Gracias</h2>
      </modal>
    </teleport>
    
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue'
  import { Time, Services } from '../types/FormTypes'
  import Modal from './Modal.vue'
 
  let name = ref('')
  let email = ref('')
  let phone = ref('')
  let time =ref<Time>('09:00 - 10:00')
  let service = ref<Services>('desarrollo-web')
  let description =  ref('')
  let showModal = ref(false)

  const handleBtn = () => {
    showModal.value = true
  }
</script>

<style scoped lang="scss">

</style>
