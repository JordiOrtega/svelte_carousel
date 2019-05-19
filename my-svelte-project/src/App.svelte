<script>
	export let name;

      function makeRequest(url, method) {
        let request = new XMLHttpRequest();
        return new Promise(function(resolve, reject) {
            // Setup listener para procesar la respuesta
            request.onreadystatechange = function() {
                // Aseguramos respuesta completa.
                if (request.readyState !== 4) return;
                // Procesamos respuesta.
                request.status >= 200 && request.status < 300 ?
                    resolve(request) :
                    reject({
                        status: request.status,
                        statusText: request.statusText
                    });
            };
            request.open(method || "GET", url, true);
            request.send();
        });
    };
	function handleClick() {
		let promise = makeRequest(https://api.jetlore.com/layouts/layout.json?cid=aacd9f9a13d8541db672d814e93f47b3&id=&&feed=bershka_all&div=null&lang=null&layout=Personalization_carrusel_rebajas&secure=false&jl_add_info=false&jl_backfill=yes);
	}
</script>

<button on:click={handleClick}>
	generate random number
</button>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}!</h1>

  {#await promise}
	    <!-- promise is pending -->
	    <p>waiting for the promise to resolve...</p>
    {:then value}
        <!-- promise was fulfilled -->
        <p>promise was fulfilled</p>
    {:catch error}
        <!-- promise was rejected -->
        <p>Something went wrong: {error.message}</p>
    {/await}
