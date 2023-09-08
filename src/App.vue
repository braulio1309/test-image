<template>
	<div>
		<h1>Generador de PDF</h1>
		<form @submit.prevent="generatePDF">
			<label for="firstName">Nombre:</label>
			<input type="text" id="firstName" v-model="firstName" required />
			<br />
			<label for="lastName">Apellido:</label>
			<input type="text" id="lastName" v-model="lastName" required />
			<br />
			<button type="submit">Generar PDF</button>
		</form>
	</div>
</template>
  
<script>
import jsPDF from 'jspdf';

export default {
	data() {
		return {
			firstName: '',
			lastName: '',
		};
	},
	methods: {
		generatePDF() {
			const pdf = new jsPDF();
			pdf.text(20, 20, 'Información del Usuario');
			pdf.text(20, 30, `Nombre: ${this.firstName}`);
			pdf.text(20, 40, `Apellido: ${this.lastName}`);
			pdf.save('formulario.pdf');
		},
	},
};
</script>
  