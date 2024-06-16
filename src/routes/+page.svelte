<script>
    import qrcode from "qrcode-generator";
    import Badge from "$lib/Badge.svelte";

    let atendeeName;
    let email;
    let twitter;
    let github;
    let showBadge;
    let qrcodeImageURL;

    clearPageState();

    function cancel() {
        clearPageState();
        document.getElementById("placeholder").innerHTML = "";
        document.getElementById("atendeeName").focus();
    }

    function generateBadge() {
        // validate input
        // escape name to a valid url format
        const encodedName = encodeURIComponent(atendeeName);
        showBadge = true;
        let qr = qrcode(0, 'L');
        let urlData = "http://localhost:5173/badge?name=" + encodedName;
        qr.addData(urlData);
        qr.make();
        qrcodeImageURL = qr.createDataURL();
    }

    function clearPageState() {
        atendeeName = "";
        email = "";
        twitter = "";
        github = "";
        showBadge = false;
        qrcodeImageURL = undefined;
    }
</script>
<h1>Badge QRcode generator</h1>
<form>
    <label for="atendeeName">Atendee name: </label>
    <input bind:value={atendeeName} id="atendeeName" name="atendeeName" type="text" required />
    <label for="email">Email: </label>
    <input bind:value={email} id="email" name="email" type="email" required size="64" maxlength="64" />
    <label for="twitter">Twitter: </label>
    <input bind:value={twitter} id="twitter" name="twitter" type="text" />
    <label for="github">Github: </label>
    <input bind:value={github} id="github" name="github" type="text" />
    <button on:click="{cancel}">Cancel</button>
    <button on:click="{generateBadge}">Create</button>
</form>

{#if showBadge }
    <Badge name={atendeeName} qrcode={qrcodeImageURL} />
{/if}
