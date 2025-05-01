<template>
    <div class="container mt-4">
        <h2 class="mb-4 text-primary fw-bold">📅 All Events</h2>

        <div class="row g-4">
            <div v-for="(event, index) in events" :key="event.id" class="col-12 col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm border-0 bg-success text-white">
                    <div class="card-body d-flex flex-column justify-content-between">
                        <div v-if="editIndex !== index">
                            <h5 class="card-title">{{ event.name }}</h5>
                            <p class="card-text mb-1"><strong>Description:</strong> {{ event.description }}</p>
                            <p class="card-text"><strong>Date:</strong> {{ event.date }}</p>

                            <div class="mt-3 d-flex flex-wrap gap-2">
                                <button @click="likeEvent(index)" class="btn btn-outline-light btn-sm">
                                    ❤️ {{ event.likes }}
                                </button>
                                <button @click="startEdit(index)" class="btn btn-light btn-sm text-info fw-bold">
                                    ✏️ Edit
                                </button>
                                <button @click="removeEvent(index)" class="btn btn-danger btn-sm">
                                    🗑️ Remove
                                </button>
                            </div>
                        </div>

                        <div v-else>
                            <div class="mb-3">
                                <label class="form-label text-white">Event Name</label>
                                <input v-model="editName" class="form-control" placeholder="Enter event name" />
                            </div>

                            <div class="mb-3">
                                <label class="form-label text-white">Description</label>
                                <input v-model="editDescription" class="form-control" placeholder="Enter event name" />
                            </div>

                            <div class="mb-3">
                                <label class="form-label text-white">Event Date</label>
                                <input v-model="editDate" type="date" class="form-control" />
                            </div>

                            <div class="d-flex flex-wrap gap-2">
                                <button @click="saveEdit(index)" class="btn btn-success btn-sm">
                                    💾 Save
                                </button>
                                <button @click="cancelEdit()" class="btn btn-secondary btn-sm">
                                    ❌ Cancel
                                </button>
                            </div>
                        </div>
                    </div>
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
            editIndex: null,
            editName: '',
            editDescription: '',
            editDate: ''
        }
    },
    methods: {
        removeEvent(index) {
            this.events.splice(index, 1)
        },
        startEdit(index) {
            this.editIndex = index
            this.editName = this.events[index].name
            this.editDescription = this.events[index].description
            this.editDate = this.events[index].date
        },
        saveEdit(index) {
            this.events[index].name = this.editName
            this.events[index].description = this.editDescription
            this.events[index].date = this.editDate
            this.editIndex = null
        },
        cancelEdit() {
            this.editIndex = null
        },
        likeEvent(index) {
            this.events[index].likes++
        }
    }
}
</script>

<style scoped>
.card {
    border-left: 5px solid #ffffff;
}
</style>
