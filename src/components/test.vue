/* <template>
	<div class="hello">
		<!-- <p v-for="(a,idx) in obj" :key="idx">{{a.name}} : {{a.Age}}</p> -->

		<input type="text" placeholder="Name" v-model="datas.name">
		<input type="text" placeholder="Age" v-model="datas.Age">
		<button @click="saveData">ADD</button>
	</div>
</template>

<script>
	import db from '../firebase/firebaseInit'
	export default {
		name: 'test',
		data() {
			return {
				obj: [],
				datas: {
					name: null,
					Age: null
				}
			}
		},
		methods: {
			getData() {
				db.collection("Product").get().then((querySnapshot) => {
					querySnapshot.forEach((doc) => {
						let a = doc.data();
						this.obj.push(a);
					});
				});
			},
			saveData() {
				db.collection("Product").add(this.datas).then((docRef) => {
						console.log("Document written with ID: ", docRef.id);
					})
			}
		},
		created() {
			this.getData();
		},
		mounted() {
			console.log(db);
			console.log(this.obj)
		},
		computed: {

		},
		watch: {

		},
	}
</script>

<style>

</style> 