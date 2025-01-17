<script setup>
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Link, usePage } from '@inertiajs/vue3';

defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const user = usePage().props.auth.user;

</script>

<template>
    <section>
        <header>
            <h2 class="text-2xl font-medium text-gray-900">
                Información del perfil
            </h2>
        </header>

        <div class="mt-6 space-y-6">
            <div>
                Nombre: {{ user.name }}
            </div>

            <div>
                Apellido: {{ user.apellido }}
            </div>

            <div>
                Teléfono: {{ user.telefono }}
            </div>

            <div>
                Correo: {{ user.email }}
            </div>

          </div>
    </section>
</template>
