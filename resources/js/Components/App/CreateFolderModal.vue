<template>
    <Modal :show="modelValue" @show="onShow" max-width="sm">
        <div class="p-6">
            <h2 class="text-lg font-medium text-gray-900">Create New Folder</h2>
            <div class="mt-6">
                <InputLabel for="FolderName" value="Folder Name" />
                <TextInput
                    ref="folderNameInput"
                    type="text"
                    id="FolderName"
                    v-model="form.name"
                    class="mt-1 block w-full"
                    :class="
                        form.errors.name
                            ? 'border-red-500 focus:border-red-500 focus:ring-red-500'
                            : ''
                    "
                    placeholder="Folder Name"
                    @keyup.enter="CreateFolder"
                />
                <InputError class="mt-2" :message="form.errors.email" />
                <div class="mt-6 flex justify-end">
                    <SecondaryButton @click="closeModal"
                        >Cancel
                    </SecondaryButton>
                    <PrimaryButton
                        class="ml-3"
                        :class="{ 'opacity-25': form.processing }"
                        @click="CreateFolder"
                        :disable="form.processing"
                        >Submit</PrimaryButton
                    >
                </div>
            </div>
        </div>
    </Modal>
</template>

<script setup>
import { nextTick, ref } from "vue";
import InputError from "../InputError.vue";
import InputLabel from "../InputLabel.vue";
import Modal from "../Modal.vue";
import PrimaryButton from "../PrimaryButton.vue";
import SecondaryButton from "../SecondaryButton.vue";
import TextInput from "../TextInput.vue";
import { useForm } from "@inertiajs/vue3";

const folderNameInput = ref(null);
const { modelValue } = defineProps({
    modelValue: Boolean,
});
const emit = defineEmits(["update:modelValue"]);
const form = useForm({
    name: "",
});

const CreateFolder = () => {
    form.post(route("folder.create"), {
        preserveScroll: true,
        onSuccess: () => {
            closeModal();
            form.reset;
        },
        onError: () => folderNameInput.value.focus(),
    });
};

const onShow = () => {
    nextTick(() => folderNameInput.value.focus());
};
const closeModal = () => {
    emit("update:modelValue");
    form.clearErrors();
    form.reset();
};
</script>

<style lang="scss" scoped></style>
