<template>
    <section>
        <div class="block">
            <b-switch v-model="showMusic"> Show Music item (using <code>v-if</code>) </b-switch>
        </div>
        <div class="block">
            <b-switch v-model="showBooks"> Show books item (by adding / removing from the array) </b-switch>
        </div>
        <b-steps v-model="activeStep">
            <template v-for="(step, index) in steps">
                <b-step-item
                    v-if="step.displayed"
                    :key="index"
                    :label="step.label">
                    {{ step.content }}
                </b-step-item>
            </template>
        </b-steps>
    </section>
</template>

<script>
    export default {
        data() {
            return {
                activeStep: 0,
                showMusic: true,
                showBooks: false
            }
        },
        computed: {
            baseSteps() {
                return [
                    {
                        label: 'Pictures',
                        content: 'Pictures: Lorem ipsum dolor sit amet.',
                        displayed: true,
                    },
                    {
                        label: 'Music',
                        content: 'Music: Lorem ipsum dolor sit amet.',
                        displayed: this.showMusic,
                    },
                    {
                        label: 'Videos',
                        content: 'Videos: Lorem ipsum dolor sit amet.',
                        displayed: true,
                    }
                ]
            },
            steps() {
                const steps = [...this.baseSteps]
                if (this.showBooks) {
                    steps.splice(steps.length - 1, 0, this.bookStep);
                }
                return steps
            },
            bookStep() {
                return {
                    label: 'Books',
                    content: 'Books: Lorem ipsum dolor sit amet.',
                    displayed: true,
                }
            }
        }
    }
</script>
