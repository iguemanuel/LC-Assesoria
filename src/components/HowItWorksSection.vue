<script setup lang="ts">
const steps = [
  {
    number: '01',
    title: 'Entre em Contato',
    description:
      'Fale conosco por WhatsApp ou telefone. Nossa equipe está pronta para ouvir seu caso.',
    icon: 'chat',
  },
  {
    number: '02',
    title: 'Análise do Caso',
    description:
      'Nossos especialistas avaliam toda a documentação e identificam os melhores caminhos para garantir seus direitos.',
    icon: 'document',
  },
  {
    number: '03',
    title: 'Receba sua Indenização',
    description:
      'Acompanhamos todo o processo até a conclusão, garantindo que você receba o que é seu por direito.',
    icon: 'money',
  },
]
</script>

<template>
  <section id="como-funciona" class="section how-it-works">
    <div class="container">
      <div class="hiw-badge">
        <span class="hiw-arrows">&#9654;</span>
        PASSO A PASSO DO PROCESSO
      </div>
      <h2 class="hiw-title">Estratégia de Trabalho</h2>

      <div class="steps">
        <template v-for="(step, index) in steps" :key="step.number">
          <div class="step-col">
            <div class="step-circle">
              <div class="step-icon">
                <!-- Chat -->
                <svg
                  v-if="step.icon === 'chat'"
                  width="36"
                  height="36"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path
                    d="M21 11.5a8.38 8.38 0 01-.9 3.8 8.5 8.5 0 01-7.6 4.7 8.38 8.38 0 01-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 01-.9-3.8 8.5 8.5 0 014.7-7.6 8.38 8.38 0 013.8-.9h.5a8.48 8.48 0 018 8v.5z"
                  />
                  <circle cx="8.5" cy="11" r="0.5" fill="currentColor" />
                  <circle cx="12" cy="11" r="0.5" fill="currentColor" />
                  <circle cx="15.5" cy="11" r="0.5" fill="currentColor" />
                </svg>
                <!-- Document -->
                <svg
                  v-if="step.icon === 'document'"
                  width="36"
                  height="36"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <rect x="3" y="3" width="18" height="18" rx="2" />
                  <line x1="9" y1="3" x2="9" y2="21" />
                  <line x1="13" y1="8" x2="17" y2="8" />
                  <line x1="13" y1="12" x2="17" y2="12" />
                  <line x1="13" y1="16" x2="15" y2="16" />
                </svg>
                <!-- Money -->
                <svg
                  v-if="step.icon === 'money'"
                  width="36"
                  height="36"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <line x1="12" y1="1" x2="12" y2="23" />
                  <path d="M17 5H9.5a3.5 3.5 0 000 7h5a3.5 3.5 0 010 7H6" />
                </svg>
              </div>
              <div class="step-number">{{ step.number }}</div>
            </div>
            <h3 class="step-title">{{ step.title }}</h3>
            <p class="step-desc">{{ step.description }}</p>
          </div>

          <!-- Connector -->
          <div v-if="index < steps.length - 1" class="step-connector">
            <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
              <path
                :d="
                  index === 0
                    ? 'M6 12 C16 12, 20 24, 24 24 C28 24, 32 36, 42 36'
                    : 'M6 36 C16 36, 20 24, 24 24 C28 24, 32 12, 42 12'
                "
                stroke="var(--color-primary)"
                stroke-width="2"
                stroke-dasharray="4 4"
                fill="none"
              />
              <polygon
                :points="index === 0 ? '38,32 44,36 38,40' : '38,8 44,12 38,16'"
                fill="var(--color-primary)"
              />
            </svg>
          </div>
        </template>
      </div>
    </div>
  </section>
</template>

<style scoped>
.how-it-works {
  background-color: var(--color-bg);
}

.hiw-badge {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  color: var(--color-primary);
  font-size: 0.8125rem;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.hiw-arrows {
  font-size: 0.625rem;
  letter-spacing: -2px;
}

.hiw-title {
  font-family: 'Playfair Display', serif;
  font-size: 2.5rem;
  font-weight: 600;
  text-align: center;
  color: var(--color-dark);
  margin-bottom: 64px;
}

.steps {
  display: flex;
  align-items: flex-start;
  justify-content: center;
}

.step-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  flex: 1;
  max-width: 300px;
}

.step-circle {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  border: 2px dashed var(--color-gray-light);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  background: var(--color-bg);
  margin-bottom: 28px;
}

.step-icon {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #2e7d32;
}

.step-number {
  position: absolute;
  bottom: -6px;
  left: -6px;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: var(--color-bg);
  border: 2px dashed var(--color-gray-light);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.875rem;
  font-weight: 700;
  color: var(--color-dark);
}

.step-connector {
  display: flex;
  align-items: center;
  padding-top: 50px;
  flex-shrink: 0;
}

.step-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.375rem;
  font-weight: 700;
  font-style: italic;
  color: var(--color-dark);
  margin-bottom: 12px;
}

.step-desc {
  font-size: 0.9375rem;
  color: var(--color-gray);
  line-height: 1.7;
  max-width: 260px;
}

@media (max-width: 768px) {
  .hiw-title {
    font-size: 1.875rem;
    margin-bottom: 40px;
  }

  .steps {
    flex-direction: column;
    align-items: center;
    gap: 40px;
  }

  .step-connector {
    display: none;
  }

  .step-circle {
    width: 130px;
    height: 130px;
  }

  .step-icon {
    width: 68px;
    height: 68px;
  }

  .step-icon svg {
    width: 30px;
    height: 30px;
  }
}
</style>
