<script setup>
import { computed, defineComponent, reactive, ref } from 'vue';
import { useDisplay } from 'vuetify';

const { xs, sm, md, lg, xlAndUp } = useDisplay();

defineComponent({
    name: 'Skills',
});

const skills = reactive({
    options: [
        {
            id: 1,
            name: 'Back-end',
        },
        {
            id: 2,
            name: 'Front-end',
        },
        {
            id: 3,
            name: 'UI',
        },
        {
            id: 4,
            name: 'DBMS',
        },
        {
            id: 5,
            name: 'DevOps/Cloud',
        },
        {
            id: 6,
            name: 'Other',
        },
    ],
    items: [
        {
            id: 1,
            option: 1,
            name: 'Python',
            experience: '3 years',
        },
        {
            id: 2,
            option: 1,
            name: 'Flask',
            experience: '3 years',
        },
        {
            id: 3,
            option: 1,
            name: 'FastAPI',
            experience: '1 year',
        },
        {
            id: 4,
            option: 1,
            name: 'Django',
            experience: '1 year',
        },
        {
            id: 5,
            option: 2,
            name: 'Vue.js',
            experience: '3 years',
        },
        {
            id: 6,
            option: 2,
            name: 'Nuxt.js',
            experience: '1.5 years',
        },
        {
            id: 7,
            option: 2,
            name: 'Vite',
            experience: '1 year',
        },
        {
            id: 8,
            option: 3,
            name: 'Tailwind',
            experience: '3 years',
        },
        {
            id: 9,
            option: 3,
            name: 'Bootstrap',
            experience: '1 year',
        },
        {
            id: 10,
            option: 4,
            name: 'PostgreSQL',
            experience: '3 years',
        },
        {
            id: 11,
            option: 4,
            name: 'MongoDB',
            experience: '1 year',
        },
        {
            id: 12,
            option: 4,
            name: 'MySQL',
            experience: '2 years',
        },
        {
            id: 13,
            option: 4,
            name: 'MariaDB',
            experience: '2 years',
        },
        {
            id: 14,
            option: 4,
            name: 'Redis',
            experience: '3 years',
        },
        {
            id: 15,
            option: 5,
            name: 'Docker',
            experience: '3 years',
        },
        {
            id: 16,
            option: 5,
            name: 'Kubernetes',
            experience: '2 years',
        },
        {
            id: 17,
            option: 5,
            name: 'Openstack',
            experience: '3 years',
        },
        {
            id: 18,
            option: 5,
            name: 'AWS',
            experience: '1 year',
        },
        {
            id: 19,
            option: 5,
            name: 'CI/CD',
            experience: '2 years',
        },
        {
            id: 20,
            option: 5,
            name: 'Ceph',
            experience: '2 years',
        },
        {
            id: 21,
            option: 6,
            name: 'Latex',
            experience: '2 years',
        },
        {
            id: 22,
            option: 6,
            name: 'MS Office',
            experience: '3 years',
        },
        {
            id: 23,
            option: 6,
            name: 'c4',
            experience: '1 year',
        },
        {
            id: 24,
            option: 6,
            name: 'PlantUML',
            experience: '1 year',
        },
    ],
});

const activeOption = ref(null);

const skillItems = computed(() =>
    activeOption.value != null ? skills.items.filter((item) => item.option === activeOption.value) : skills.items,
);

const toggleOption = (option) => (activeOption.value = activeOption.value === option.id ? null : option.id);
</script>
<template>
    <div class="technical-skills">
        <h5 class="text-h5 text-uppercase text-center text-deep-purple-accent-1">Technical skills</h5>
        <v-slide-group show-arrows center-active class="mt-3">
            <v-slide-group-item v-for="option in skills.options" :key="option.id" v-slot="{ isSelected, toggle }">
                <v-btn
                    class="ma-2"
                    rounded
                    :color="option.id === activeOption ? 'deep-purple-accent-1' : undefined"
                    @click="toggleOption(option)"
                >
                    {{ option.name }}
                </v-btn>
            </v-slide-group-item>
        </v-slide-group>
        <v-item-group selected-class="bg-deep-purple-accent-1" class="technical-skills__row">
            <v-row>
                <v-col
                    v-for="skill in skillItems"
                    :key="skill.id"
                    :cols="xs ? 12 : sm ? 6 : md || lg ? 4 : xlAndUp ? 3 : undefined"
                >
                    <v-item v-slot="{ isSelected, selectedClass, toggle }">
                        <v-card :class="['technical-skills__item', selectedClass]" @click="toggle">
                            <div class="text-h5 text-center">{{ isSelected ? skill.experience : skill.name }}</div>
                        </v-card>
                    </v-item>
                </v-col>
            </v-row>
        </v-item-group>
    </div>
</template>

<style scoped>
.technical-skills__row {
    display: flex;
    margin-top: 24px;
}

.technical-skills__item {
    display: flex;
    flex: 0 1 25%;
    align-items: center;
    justify-content: center;
    text-align: center;
    height: 80px;
    user-select: none;
}
</style>
