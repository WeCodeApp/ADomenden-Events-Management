<template>
    <!-- Corrected Button trigger modal -->
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
        <i class="bi bi-gear me-2"></i> Manage Events
    </button>


    <!-- Corrected Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="eventModal" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="eventModal">Add Event</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form @submit.prevent="addNewEvent">
                        <div class="mb-3">
                            <input v-model="name" class="form-control" placeholder="Event Name" required />
                        </div>
                        <div class="mb-3">
                            <textarea v-model="description" class="form-control"
                                placeholder="Type your description here..." required>

        </textarea>
                        </div>

                        <div class="mb-3">
                            <input v-model="date" type="date" class="form-control" required />
                        </div>
                        <button type="submit" class="btn btn-success">Add Event</button>
                    </form>


                </div>

            </div>
        </div>
    </div>


</template>

<script>
export default {
    props: ['events'],
    data() {
        return {
            name: '',
            description: '',
            date: ''
        }
    },
    methods: {
        addNewEvent() {
            const newEvent = {
                id: Date.now(),
                name: this.name,
                description: this.description,
                date: this.date,
                likes: 0 // New event starts with 0 likes
            }
            this.events.push(newEvent)
            this.name = ''
            this.description = ''
            this.date = ''

        }
    }
}
</script>