<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 flex items-center justify-center p-4">
    <div class="w-full max-w-md">
      <!-- Card do formulário -->
      <div class="bg-white rounded-lg shadow-lg p-8">
        <!-- Cabeçalho -->
        <div class="text-center mb-8">
          <h1 class="text-3xl font-bold text-gray-800 mb-2">Esqueci minha senha</h1>
          <p class="text-gray-600">Digite seu email para receber as instruções de redefinição</p>
        </div>

        <!-- Formulário -->
        <form class="space-y-6">
          <!-- Email input -->
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
              Email
            </label>
            <BaseInput
              id="email"
              type="email"
              placeholder="Digite seu email"
            />
          </div>

          <!-- Botão enviar -->
          <BaseButton
            type="submit"
            variant="primary"
            size="md"
            class="w-full"
          >
            Enviar email de redefinição
          </BaseButton>
        </form>

        <!-- Link para login -->
        <div class="mt-6 text-center">
          <p class="text-gray-600 text-sm">
            Lembrou sua senha?
            <NuxtLink
              to="/login"
              class="font-semibold text-indigo-600 hover:text-indigo-700 transition-colors"
            >
              Voltar para login
            </NuxtLink>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Apenas UI, sem lógica por enquanto
</script>
