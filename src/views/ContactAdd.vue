<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <AddContactForm :contact="contact" @submit:contact ="createContact"/>
        <p>{{ message }}</p>
    </div>
</template>
<script>
import AddContactForm from "@/components/AddContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: { AddContactForm },
    data() {
        return {
            contact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: "",
            },
            message: "",
        }
    },
    methods: {
        async createContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    }
}
</script>