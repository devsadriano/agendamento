<template>
  <BaseModal
    v-model="modalVisible"
    title="Novo Usuário"
    confirm-text="Criar Conta"
    cancel-text="Cancelar"
    confirm-variant="primary"
    :loading="loading"
    @confirm="handleConfirm"
    @close="handleClose"
  >
    <form @submit.prevent="handleConfirm" class="space-y-4">
      <!-- Nome -->
      <div>
        <label for="novo-usuario-nome" class="block text-sm font-medium text-gray-700 mb-1">
          Nome *
        </label>
        <BaseInput
          id="novo-usuario-nome"
          v-model="form.nome"
          type="text"
          placeholder="Digite o nome do usuário"
          :disabled="loading"
          required
        />
      </div>

      <!-- Email -->
      <div>
        <label for="novo-usuario-email" class="block text-sm font-medium text-gray-700 mb-1">
          Email *
        </label>
        <BaseInput
          id="novo-usuario-email"
          v-model="form.email"
          type="email"
          placeholder="Digite o email do usuário"
          :disabled="loading"
          required
        />
      </div>

      <!-- Senha -->
      <div>
        <label for="novo-usuario-senha" class="block text-sm font-medium text-gray-700 mb-1">
          Senha *
        </label>
        <BaseInput
          id="novo-usuario-senha"
          v-model="form.senha"
          type="password"
          placeholder="Digite a senha do usuário"
          :disabled="loading"
          required
        />
      </div>
    </form>
  </BaseModal>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import BaseModal from '~/components/BaseModal.vue'
import BaseInput from '~/components/BaseInput.vue'

interface Props {
  modelValue: boolean
}

const props = defineProps<Props>()

const emit = defineEmits<{
  'update:modelValue': [value: boolean]
  confirm: [data: { nome: string; email: string; senha: string }]
  close: []
}>()

// Estados
const loading = ref(false)

// Formulário
const form = ref({
  nome: '',
  email: '',
  senha: ''
})

// Computed
const modalVisible = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value)
})

// Métodos
const handleConfirm = () => {
  // Por enquanto apenas fecha o modal
  // A ação será implementada depois
  emit('confirm', { ...form.value })
}

const handleClose = () => {
  // Limpar formulário ao fechar
  form.value = {
    nome: '',
    email: '',
    senha: ''
  }
  emit('close')
}

// Expor métodos para uso externo
const setLoading = (value: boolean) => {
  loading.value = value
}

defineExpose({
  setLoading
})
</script>
