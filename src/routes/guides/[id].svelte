<script context="module">
    export async function load({ fetch, params }) {
        const id   = params.id;
        const resp = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
        const guide = await resp.json();

        if (resp.ok) {
            return {
                props: {
                    guide
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
    export let guide;
</script>


<div class="guide mt-10 mx-4">

    <h2 class="text-xl font-bold mb-6"> {guide.title} </h2>
    <p> {guide.body} </p>

    <a class="text-blue-500 mr-3" href="/">Home</a>
    <a class="text-blue-500" href="/guides">Guide</a>

</div>

