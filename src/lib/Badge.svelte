<script>
    export let name;
    export let qrcode;
</script>
<div>
    <p>Here's the badge!</p>
    <img src="avatar_placeholder_large.png" />
    <p>{name}</p>
    <img src={qrcode} />
</div>

