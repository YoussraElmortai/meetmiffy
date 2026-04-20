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

		//sizes
		const sizes = {
			width: window.innerWidth,
			height: window.innerHeight
		};

		//light

		const light = new THREE.HemisphereLight(0xffffbb, 0x080820, 1);
		scene.add(light);

		//camera
		const camera = new THREE.PerspectiveCamera(40, sizes.width / sizes.height);
		camera.position.z = 15;

		//render

		const canvas = document.querySelector('.webgl');
		const renderer = new THREE.WebGLRenderer({ canvas });

		renderer.setSize(sizes.width, sizes.height);
		renderer.render(scene, camera);

		// resize

		window.addEventListener('resize', () => {
			sizes.width = window.innerWidth;
			sizes.height = window.innerHeight;

			camera.aspect = sizes.width / sizes.height;
			camera.updateProjectionMatrix();
			renderer.setSize(sizes.width, sizes.height);

			renderer.render(scene, camera); // Re-render after  resize otherwise resize doesnt work?
		});
	});
</script>

<section class="about">
	<a class="button" href="/">About miffy</a> <a class="button" href="/">About Bruna</a>
	<button>Button</button>
</section>

<section>
	<canvas class="webgl"> </canvas>
</section>

<style>
</style>
