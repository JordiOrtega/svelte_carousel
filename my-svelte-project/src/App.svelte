<script>
	export let name;
    let promise = makeRequest("https://api.flickr.com/services/feeds/photos_public.gne?tags=cat&tagmode=any&format=json");
        function makeRequest(url){
          fetch(url,{mode:'no-cors',contentType: 'application/json'}) // Call the fetch function passing the url of the API as a parameter
            .then(function(response) {
                // Your code for handling the data you get from the API
                console.log(response.status, response);

            })
            .catch(function() {
                // This is where you run code if the server returns any errors
                console.log('error');
            });
        }
	function handleClick() {
        //promise = makeRequest("https://api.jetlore.com/layouts/layout.json?cid=aacd9f9a13d8541db672d814e93f47b3&id=&&feed=bershka_all&div=null&lang=null&layout=PruebaCaro111&secure=true&jl_add_info=true&jl_response=full&jl_backfill=yes");
		promise = makeRequest("https://api.flickr.com/services/feeds/photos_public.gne?tags=tsuboniwa,garden&format=json");
        
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
