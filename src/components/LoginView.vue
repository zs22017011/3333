<script>
import { useRouter } from 'vue-router'

const router = useRouter()

function goToProducts() {
  router.push('/products')
}
</script>

<template>
  <div class="container">
    <div class="loginBox">
      <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
      <h1 class="MainTitle">Ingresar</h1>
      <main>
        <form class="login-form">
          <label for="username">Usuario</label>
          <input
              type="text"
              id="username"
              name="username"
              placeholder="Ingresa tu nombre de usuario"
              required
          />

          <label for="password">Contraseña</label>
          <input
              type="password"
              id="password"
              name="password"
              placeholder="Ingresa tu contraseña"
              required
          />

          <button type="submit">Entrar</button>
          <router-link to="/products" aria-label="Regístrate aquí">Products view</router-link>
        </form>
      </main>

      <div class="register">
        <p>¿No tienes una cuenta?</p> <router-link to="/register" aria-label="Regístrate aquí">Regístrate aquí</router-link>
      </div>

    </div>

  </div>

</template>

<style scoped>

.container {
  min-width: 80vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.loginBox {
  min-width: fit-content;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  background-color: #f2f2f2;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

header {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: fit-content;
  width: fit-content;
  text-align: center;
}

.MainTitle {
  font-size: 2.5rem;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 1px;
  padding-bottom: 2rem;
  background: linear-gradient(90deg, #42b983, #57799c);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: background 5s ease-in-out;
}


.MainTitle:hover {
  background: linear-gradient(90deg, #57799c, #42b983);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}


.login-form {
  width: 100%;
  max-width: 300px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.login-form h2 {
  text-align: center;
  margin-bottom: 1.5rem;
}

.login-form label {
  font-weight: bold;
}

.login-form input {
  padding: 0.5rem;
  border: 1px solid #cccccc;
  border-radius: 6px;
  background: #ffffff;
}

.login-form button {
  padding: 0.75rem;
  border: none;
  border-radius: 4px;
  background: #42b983;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
}

.login-form button:hover {
  background: #36a273;
}


.register{
  padding: 2rem;
  text-align: center;
}

.register a {
  color: #42b983;
  font-weight: bold;
  text-decoration: none;
}

.register a:hover {
  text-decoration: underline;
  color: #36a273;
}

</style>
<script setup lang="ts">
</script>