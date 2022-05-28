<script context="module">
    export async function load({ fetch }) {
        const resp   = await fetch('https://jsonplaceholder.typicode.com/posts');
        const guides = await resp.json();
        
        if (resp.ok) {
            return {
                props: {
                    guides
                }
            }
        }

        return {
            status: resp.status,
            error: new Error('Not found')
        }
    }
</script>


<script>
    export let guides;
</script>

<div class="guides px-2 mt-10">
    
    <ul>

        {#each guides as guide}
            <li class="my-4">
                <a sveltekit:prefetch class="underline" href={`/guides/${guide.id}`}> {guide.title} </a>
            </li>
        {/each}

    </ul>

    <a class="text-blue-500" href="/">Home</a>
</div>