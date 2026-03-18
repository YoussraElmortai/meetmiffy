<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';

	onMount(() => {
		// scene

		const scene = new THREE.Scene();

		//create a sphere
		// spheregeometry (size, width , height)
		const geometry = new THREE.SphereGeometry(3, 64, 64);
		const material = new THREE.MeshStandardMaterial({
			color: 'hotpink'
		});

		const mesh = new THREE.Mesh(geometry, material);
		scene.add(mesh);

		//light

		// const light = new THREE.PointLight(0xffffff, 1, 100);
		// light.position.set(10, 10, 10);
		// scene.add(light);

		const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
		scene.add(ambientLight);

		//camera
		const camera = new THREE.PerspectiveCamera(45, 800 / 600, 0.1, 1000);
		camera.position.z = 10;

		//render

		const canvas = document.querySelector('.webgl');
		const renderer = new THREE.WebGLRenderer({ canvas });

		renderer.setSize(800, 600);
		renderer.render(scene, camera);
	});
</script>

<section class="hero">
	<h2>Dick Bruna</h2>

	<canvas class="webgl"> </canvas>
</section>

<section class="about">
	<ul>
		<li>
			<h3>Dick Bruna</h3>
			<article>creator of miffy</article>
		</li>
		<li>
			<h3>Dick Bruna</h3>
			<article>creator of miffy</article>
		</li>
		<li>
			<h3>Dick Bruna</h3>
			<article>creator of miffy</article>
		</li>
	</ul>
</section>

<style>
	.about {
		& ul {
			display: flex;
			flex-flow: row wrap;
			justify-content: space-around;
		}

		& li {
			list-style-type: none;
		}
	}
</style>
