<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const showPassword = ref(false)

const canSubmit = () => email.value.trim().length > 0 && password.value.length > 0
</script>
<template>
  <div class="login-page">
    <header class="login-page__brand">
      <span class="login-page__logo" />
      <span>MedConsult App</span>
    </header>

    <main class="login-page__main">
      <form class="login-card card" @submit.prevent="handleSubmit">
        <h1 class="login-card__title">Logowanie</h1>
        <p class="login-card__subtitle">Zaloguj się, aby otworzyć panel</p>

        <label class="field-label" for="email">E-mail</label>
        <input
          id="email"
          v-model="email"
          class="field-input"
          type="email"
          autocomplete="username"
          placeholder="jan.kowalski@firma.pl"
        />

        <label class="field-label" for="password" style="margin-top: 14px">Hasło</label>
        <div class="login-card__password-row">
          <input
            id="password"
            v-model="password"
            class="field-input"
            :type="showPassword ? 'text' : 'password'"
            autocomplete="current-password"
            placeholder="••••••••••"
          />
          <button
            type="button"
            class="login-card__toggle"
            :aria-label="showPassword ? 'Ukryj hasło' : 'Pokaż hasło'"
            @click="showPassword = !showPassword"
          >
            {{ showPassword ? 'Ukryj' : 'Pokaż' }}
          </button>
        </div>

        <!--
        <p v-if="auth.error" class="field-error">{{ auth.error }}</p>
        -->

        <!--<button
          class="btn btn-primary login-card__submit"
          type="submit"
          :disabled="!canSubmit() || auth.loading"
        >-->
        <!-- {{ auth.loading ? 'Logowanie...' : 'Zaloguj się' }}
        </button>-->

        <a class="login-card__forgot" href="#">Nie pamiętasz hasła?</a>

        <div class="login-card__hint">
          <p><strong>Konta demo (dane mockowe):</strong></p>
          <p>Pacjent: jan.kowalski@pacjent.pl / pacjent123</p>
          <p>Konsultant: anna.nowak@medconsult.pl / konsultant123</p>
        </div>
      </form>
    </main>

    <footer class="login-page__footer">
      © MedConsult — panel konsultanta zintegrowany z Salesforce
    </footer>
  </div>
</template>

<style scoped>
.login-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: var(--color-bg);
}

.login-page__brand {
  height: 56px;
  background: var(--color-navy);
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 20px;
  color: #fff;
  font-weight: 700;
  flex-shrink: 0;
}

.login-page__logo {
  width: 22px;
  height: 22px;
  border-radius: 50%;
  background: #4f9dde;
}

.login-page__main {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px 16px;
}

.login-card {
  width: 100%;
  max-width: 340px;
  padding: 32px;
  display: flex;
  flex-direction: column;
}

.login-card__title {
  margin: 0;
  font-size: 20px;
  text-align: center;
  color: var(--color-navy);
}

.login-card__subtitle {
  margin: 6px 0 24px;
  font-size: 12px;
  text-align: center;
  color: var(--color-text-muted);
}

.login-card__password-row {
  position: relative;
}

.login-card__toggle {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  color: var(--color-blue);
  font-size: 11px;
  font-weight: 600;
}

.login-card__submit {
  margin-top: 20px;
  width: 100%;
  padding: 12px;
}

.login-card__forgot {
  margin-top: 16px;
  text-align: center;
  font-size: 12px;
  color: var(--color-blue);
  text-decoration: underline;
}

.login-card__hint {
  margin-top: 24px;
  padding-top: 16px;
  border-top: 1px dashed var(--color-border);
  font-size: 11px;
  color: var(--color-text-faint);
  line-height: 1.6;
}

.login-card__hint p {
  margin: 0;
}

.login-page__footer {
  text-align: center;
  font-size: 11px;
  color: var(--color-text-faint);
  padding: 16px;
}
</style>
