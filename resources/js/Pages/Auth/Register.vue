<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    apellido: '',
    telefono: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const sanitizeInput = (e) => {
    e.target.value = e.target.value.replace(/[^+\d\s-]/g, '');
    form.telefono = e.target.value;
};

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};

</script>

<template>
    <GuestLayout>
        <Head title="Register" />

        <div class="mb-4 text-3xl text-center">
          Registro
        </div>

        <form @submit.prevent="submit">
            <div>
                <InputLabel for="name" value="Nombre" />

                <TextInput
                    id="name"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.name"
                    required
                    autofocus
                    autocomplete="name"
                />

                <InputError class="mt-2" :message="form.errors.name" />
            </div>

            <div class="mt-4">
                <InputLabel for="apellido" value="Apellido" />

                <TextInput
                    id="apellido"
                    type="text"
                    class="mt-1 block w-full"
                    v-model="form.apellido"
                    required
                    autofocus
                    autocomplete="apellido"
                />

                <InputError class="mt-2" :message="form.errors.apellido" />
            </div>

            <div class="mt-4">
                <InputLabel for="telefono" value="Teléfono" />

                <TextInput
                    id="telefono"
                    type="text"
                    maxlength="16"
                    class="mt-1 block w-full"
                    @input="sanitizeInput"
                    placeholder="+999 9999 9999"
                    v-model="form.telefono"
                    required
                    autofocus
                    autocomplete="telefono"
                />

                <InputError class="mt-2" :message="form.errors.telefono" />
            </div>

            <div class="mt-4">
                <InputLabel for="email" value="Correo" />

                <TextInput
                    id="email"
                    type="email"
                    class="mt-1 block w-full"
                    v-model="form.email"
                    placeholder="correo@dominio.com"
                    required
                    autocomplete="username"
                />

                <InputError class="mt-2" :message="form.errors.email" />
            </div>

            <div class="mt-4">
                <InputLabel for="password" value="Contraseña" />

                <TextInput
                    id="password"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password"
                    required
                    autocomplete="new-password"
                />

                <InputError class="mt-2" :message="form.errors.password" />
            </div>

            <div class="mt-4">
                <InputLabel
                    for="password_confirmation"
                    value="Confirmar contraseña"
                />

                <TextInput
                    id="password_confirmation"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password_confirmation"
                    required
                    autocomplete="new-password"
                />

                <InputError
                    class="mt-2"
                    :message="form.errors.password_confirmation"
                />
            </div>

            <div class="mt-4 flex items-center justify-end">
                <Link
                    :href="route('login')"
                    class="rounded-md text-sm text-gray-600 underline hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                >
                    ¿Ya estás registrado?
                </Link>

                <PrimaryButton
                    class="ms-4"
                    :class="{ 'opacity-25': form.processing }"
                    :disabled="form.processing"
                >
                    Registrar
                </PrimaryButton>
            </div>
        </form>
    </GuestLayout>
</template>