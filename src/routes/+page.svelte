<script>
    import qrcode from "qrcode-generator";

    let name = "";
    let email = "";
    let twitter = "";
    let github = "";

    function cancel() {
        name = "";
        email = "";
        twitter = "";
        github = "";
    }

    function generateBadge() {
        let qr = qrcode(4, 'L');
        qr.addData("Hi");
        qr.make();
        document.getElementById("placeholder").innerHTML = qr.createImgTag();
    }
</script>
<h1>Badge QRcode generator</h1>
<form>
    <label for="name">Name: </label>
    <input bind:value={name} name="name" type="text" required />
    <label for="email">Email: </label>
    <input bind:value={email} name="email" type="text" required />
    <label for="twitter">Twitter: </label>
    <input bind:value={twitter} name="twitter" type="text" />
    <label for="github">Github: </label>
    <input bind:value={github} name="github" type="text" />
    <button on:click="{cancel}">Cancel</button>
    <button on:click="{generateBadge}">Create</button>
</form>
<h2>
    debug
</h2>
<p>{name}</p>
<p>{email}</p>
<p>{twitter}</p>
<p>{github}</p>
<div id="placeholder"></div>

