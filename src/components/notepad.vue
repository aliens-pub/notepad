<template>
  <div class="notepad">
    <h2>간단 메모장</h2>
    <textarea v-model="newNote" placeholder="메모를 입력하세요..."></textarea>
    <button @click="addNote">메모 추가</button>
    <div class="notes-list">
      <h3>저장된 메모:</h3>
      <ul>
        <li v-for="(note, index) in notes" :key="index">
          {{ note }}
          <button @click="deleteNote(index)" class="delete-button">삭제</button>
        </li>
      </ul>
      <p v-if="notes.length === 0">저장된 메모가 없습니다.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NotePad',
  data() {
    return {
      newNote: '',
      notes: []
    };
  },
  methods: {
    addNote() {
      if (this.newNote.trim() !== '') {
        this.notes.push(this.newNote.trim());
        this.newNote = ''; // 입력 필드 초기화
      }
    },
    deleteNote(index) {
      this.notes.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.notepad {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
textarea {
  width: 100%;
  min-height: 100px;
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
}
button {
  padding: 10px 15px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-bottom: 20px;
}
button:hover {
  background-color: #369f73;
}
.notes-list ul {
  list-style-type: none;
  padding: 0;
}
.notes-list li {
  background-color: #f9f9f9;
  padding: 10px;
  margin-bottom: 8px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.delete-button {
  background-color: #e74c3c;
  font-size: 0.8em;
  padding: 5px 8px;
  margin-bottom: 0;
}
.delete-button:hover {
  background-color: #c0392b;
}
</style> 