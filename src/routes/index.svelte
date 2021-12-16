<script lang="ts">
	interface Iobjeto {
		letra: string;
		simbolos: any;
		decoration?: string;
		background?: string;
	}
	let texto = '';
	let textoSeparado: string[];
	let decodificado: string;

	const colores = [
		'pink-700',
		'orange-100',
		'violet-500',
		'cyan-400',
		'rose-400',
		'cyan-200',
		'yellow-400',
		'zinc-300',
		'gray-200',
		'green-400',
		'purple-700',
		'slate-100',
		'violet-700',
		'emerald-200',
		'green-700',
		'fuchsia-400',
		'emerald-100',
		'gray-100',
		'green-100',
		'slate-400',
		'cyan-200',
		'rose-900',
		'gray-700',
		'fuchsia-700',
		'amber-400',
		'sky-200',
		'indigo-400',
		'zinc-100',
		'lime-400',
		'slate-700',
		'purple-300',
		'lime-700',
		'lime-100',
		'rose-700',
		'red-800',
		'teal-100',
		'indigo-700',
		'orange-400',
		'sky-700',
		'pink-500',
		'cyan-800',
		'emerald-600',
		'red-400',
		'teal-400',
		'orange-100',
		'sky-500'
	];

	const diccionario: Iobjeto[] = [
		{ letra: 'a', simbolos: ['1', '6', '11'] },
		{ letra: 'e', simbolos: ['2', '7', '12'] },
		{ letra: 'i', simbolos: ['3', '8', '13'] },
		{ letra: 'o', simbolos: ['4', '9', '14'] },
		{ letra: 'u', simbolos: ['5', '10', '15'] },
		{ letra: 'b', simbolos: ['16'] },
		{ letra: 'c', simbolos: ['17'] },
		{ letra: 'ch', simbolos: ['18'] },
		{ letra: 'd', simbolos: ['19'] },
		{ letra: 'f', simbolos: ['20'] },
		{ letra: 'g', simbolos: ['21'] },
		{ letra: 'h', simbolos: ['22'] },
		{ letra: 'j', simbolos: ['23'] },
		{ letra: 'k', simbolos: ['24'] },
		{ letra: 'l', simbolos: ['25'] },
		{ letra: 'll', simbolos: ['26'] },
		{ letra: 'm', simbolos: ['27', '28'] },
		{ letra: 'n', simbolos: ['29', '30', '31'] },
		{ letra: 'p', simbolos: ['32'] },
		{ letra: 'q', simbolos: ['33'] },
		{ letra: 'r', simbolos: ['34', '35'] },
		{ letra: 's', simbolos: ['36'] },
		{ letra: 't', simbolos: ['37'] },
		{ letra: 'v', simbolos: ['38'] },
		{ letra: 'w', simbolos: ['39'] },
		{ letra: 'x', simbolos: ['40'] },
		{ letra: 'y', simbolos: ['41'] },
		{ letra: 'z', simbolos: ['42'] },
		{ letra: ' ', simbolos: ['43'] }
	];

	for (let i = 0; i < diccionario.length; i++) {
		diccionario[i].decoration = 'decoration-' + colores[i];
		diccionario[i].background = 'hover:bg-' + colores[i];
	}

	$: {
		textoSeparado = texto.split(' ');
		let cadena = '';
		for (let letra = 0; letra < textoSeparado.length; letra++) {
			const caracter = simboloACaracter(textoSeparado[letra]);
			if (caracter !== undefined) {
				cadena += caracter;
			} else {
				cadena += '🚫';
			}
		}
		decodificado = cadena;
	}

	const simboloACaracter = (simbolo: any) => {
		if (isNaN(simbolo)) return simbolo;
		return diccionario.find((objeto) => objeto.simbolos.indexOf(simbolo) !== -1)?.letra;
	};
</script>

<main>
	<!-- COLORES PARA JIT -->
	<div class="hidden">
		<p class="hover:bg-pink-700">.</p>
		<p class="hover:bg-orange-100">.</p>
		<p class="hover:bg-violet-500">.</p>
		<p class="hover:bg-cyan-400">.</p>
		<p class="hover:bg-rose-400">.</p>
		<p class="hover:bg-cyan-200">.</p>
		<p class="hover:bg-yellow-400">.</p>
		<p class="hover:bg-zinc-300">.</p>
		<p class="hover:bg-gray-200">.</p>
		<p class="hover:bg-green-400">.</p>
		<p class="hover:bg-slate-100">.</p>
		<p class="hover:bg-purple-700">.</p>
		<p class="hover:bg-emerald-200">.</p>
		<p class="hover:bg-violet-700">.</p>
		<p class="hover:bg-green-700">.</p>
		<p class="hover:bg-gray-100">.</p>
		<p class="hover:bg-green-100">.</p>
		<p class="hover:bg-slate-400">.</p>
		<p class="hover:bg-cyan-200">.</p>
		<p class="hover:bg-rose-900">.</p>
		<p class="hover:bg-gray-700">.</p>
		<p class="hover:bg-fuchsia-700">.</p>
		<p class="hover:bg-amber-400">.</p>
		<p class="hover:bg-sky-200">.</p>
		<p class="hover:bg-indigo-400">.</p>
		<p class="hover:bg-zinc-100">.</p>
		<p class="hover:bg-lime-400">.</p>
		<p class="hover:bg-slate-700">.</p>
		<p class="hover:bg-purple-300">.</p>
		<p class="hover:bg-rose-700">.</p>
		<p class="hover:bg-red-800">.</p>
		<p class="hover:bg-indigo-700">.</p>
		<p class="hover:bg-">.</p>
		<p class="hover:bg-">.</p>
		<p class="hover:bg-">.</p>
	</div>

	<!-- COLUMNAS -->
	<div class="grid grid-cols-1 md:grid-cols-12 container">
		<!-- TABLA DE EQUIVALENCIAS -->
		<div class="container text-center md:col-span-4 px-8 pt-8 flex flex-col">
			<h1 class="text-3xl text-stone-600 pb-8">Tabla de equivalencias:</h1>
			<div class="flex flex-col">
				<div class="-my-2 overflow-x-hidden sm:-mx-6 lg:-mx-8">
					<div class="py-2 align-middle inline-block sm:px-6 lg:px-8">
						<div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
							<table class="w-full divide-y divide-gray-200">
								<thead class="bg-gray-50">
									<tr>
										<th
											scope="col"
											class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
										>
											Letra
										</th>
										<th
											scope="col"
											class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
										>
											Símbolo(s)
										</th>
									</tr>
								</thead>
								<tbody class="bg-white divide-y divide-gray-200">
									{#each diccionario as { letra, simbolos, decoration, background }, i}
										<tr class={`${background} cursor-pointer`}>
											<td
												class={`px-6 py-4 whitespace-nowrap text-sm text-gray-500 underline decoration-wavy font-bold decoration-1 w-8 decoration-${colores[i]}`}
											>
												{letra}
											</td>
											<td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
												{simbolos}
											</td>
										</tr>
									{/each}
								</tbody>
							</table>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- DECODIFICACIÓN -->
		<div class="container text-center md:col-span-8 p-8 flex flex-col">
			<h1 class="text-3xl text-stone-600 pb-8">Mensaje:</h1>

			<div class="mb-8">
				<p class="text-stone-500">
					Para decodificar el mensaje, cada símbolo debe estar separado por un espacio (" ").
				</p>
				<textarea
					id="about"
					name="about"
					rows="3"
					class="shadow-sm focus:ring-indigo-500 p-4 focus:border-cyan-500 mt-1 block w-full sm:text-sm border border-gray-300 rounded-md"
					placeholder="31 30 10 9 6 42 11 13 34"
					bind:value={texto}
				/>
			</div>

			<div>
				<h1 class="text-3xl text-stone-600 pb-8">Mensaje decodificado:</h1>
				{#if decodificado && decodificado !== ''}
					<div class="min-w-full border-2 border-gray-300 rounded p-4 text-justify text-stone-500">
						<p>{decodificado}</p>
					</div>
				{/if}
			</div>
		</div>
	</div>
</main>

<footer class="w-full mt-8 p-4 bg-slate-200 text-center text-stone-500">
	Hecho con ❤ por Alvarado Bolaños Fernando Enrique y Vázquez García Pablo Alan
</footer>
