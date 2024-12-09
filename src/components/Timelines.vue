<script setup>
import { defineComponent, reactive } from 'vue';

defineComponent({
    name: 'Timelines',
});

const timelines = reactive([
    {
        id: 0,
        icon: 'mdi-book-education',
        color: 'cyan lighten-1',
        title: 'Chittagong University of Engineering & Technology',
        position: 'Computer Science & Engineering',
        period: 'FEB 2016 — AUG 2022',
        description: 'Bachelor of Science',
    },
    {
        id: 1,
        icon: 'mdi-briefcase-variant',
        color: 'amber darken-1',
        title: 'Intercloud Limited',
        position: 'Software Engineer (Cloud Software)',
        period: 'JUN 2021 — DEC 2022',
        description: 'Developed and deployed high-impact cloud services and integrations for Brilliant Cloud Platform, first public cloud of Bangladesh',
    },
    {
        id: 2,
        icon: 'mdi-briefcase-variant',
        color: 'blue-darken-3',
        title: 'Nexgen Cloud Limited',
        position: 'Junior Developer',
        period: 'DEC 2022 — JUL 2024',
        description: 'Engineered scalable API solutions and real-time systems for Nexgen Cloud Limited, powering GPU-as-a-Service, unified infrastructure access, stock reporting, and dynamic pricing for 100k+ VMs.',
    },
    {
        id: 3,
        icon: 'mdi-briefcase-variant',
        color: 'blue-grey',
        title: '',
        position: 'Solutions Architect',
        period: 'JUL 2024 — PRESENT',
        description: 'Driving technical strategy and designing scalable cloud-native solutions at Nexgen Cloud, with expertise in API interfaces, distributed systems, and optimizing infrastructure for a fast-growing GPUaaS platform.',
    },
]);
</script>

<template>
    <div class="timeline mt-5">
        <h5 class="text-h5 text-uppercase text-center text-deep-purple-accent-1">Education & work</h5>
        <v-timeline class="mt-5">
            <v-timeline-item
                v-for="timeline in timelines"
                :key="timeline.id"
                :dot-color="timeline.color"
                :icon="timeline.icon"
                size="large"
            >
                <template v-slot:opposite>
                    <div
                        :class="`pt-1 headline font-weight-bold text-button text-${timeline.color}`"
                        v-text="timeline.period"
                    ></div>
                </template>
                <div>
                    <h2 :class="`mt-n1 headline font-weight-light mb-4 text-${timeline.color}`">
                        {{ timeline.title }}
                    </h2>
                    <h5 :class="`text-button text-${timeline.color}`">{{ timeline.position }}</h5>
                    <span class="text-subtitle-2">{{ timeline.description }}</span>
                </div>
            </v-timeline-item>
        </v-timeline>
    </div>
</template>
