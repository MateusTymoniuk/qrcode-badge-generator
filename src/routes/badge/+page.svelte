<script>
    import { page } from '$app/stores';

    const hasParams = $page.url.searchParams.has("name");
    const name = $page.url.searchParams.get("name");

    let email;
    if ($page.url.searchParams.has("email")) {
        email = $page.url.searchParams.get("email");
    }

    let github;
    if ($page.url.searchParams.has("github")) {
        github = $page.url.searchParams.get("github");
    }

    let twitter;
    if ($page.url.searchParams.has("twitter")) {
        twitter = $page.url.searchParams.get("twitter");
    }
</script>

<h2>Atendee name:</h2>
<p>{name}</p>
<h2>Email:</h2>
<p>{email}</p>
<h2>Github profile:</h2>
<a href="https://github.com/{github}">{github}</a>
<h2>Twitter profile:</h2>
<a href="https://x.com/{twitter}">{twitter}</a>
