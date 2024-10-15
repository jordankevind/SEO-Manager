<!-- src/routes/+page.svelte -->
<script>
    // Importing global styles or components could go here if needed
</script>

<h1>Web apps are so powerful</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<!-- Here begins the estimator tool from your existing HTML -->
<div class="estimator">
    <h2>Building Cost Estimator</h2>
    <label for="a">Area:</label>
    <select id="a">
        <option value="800">800 sqft</option>
        <option value="1600">1600 sqft</option>
        <option value="3200">3200 sqft</option>
    </select>
    <label for="f">Floors:</label>
    <select id="f">
        <option value="1">1</option>
        <option value="2">2</option>
    </select>
    <label for="b">Base:</label>
    <select id="b">
        <option value="s">Stem Wall</option>
        <option value="p">Pole (-25%)</option>
    </select>
    <label for="m">Frame:</label>
    <select id="m">
        <option value="w">Wood</option>
        <option value="t">Steel (+15%)</option>
    </select>
    <button on:click={estimateCost}>Estimate</button>
    <div id="r"></div>
</div>

<script>
    // This script could be moved to a separate file or kept here for simplicity
    function estimateCost() {
        // The function content remains the same, but note:
        // - If moving this to a separate .js or .ts file, you might need to export this function
        // - In Svelte, reactive updates might be handled differently, but for this basic example, direct DOM manipulation works
        const a = +document.getElementById('a').value,
              f = +document.getElementById('f').value,
              b = document.getElementById('b').value,
              m = document.getElementById('m').value,
              t = f * a,
              s = [1, 0.9, 0.75],
              d = s[Object.keys(s).find(k => a >= k * 800)] || 1,
              e = 70 * d,
              g = {s: 10, p: 7.5},
              h = {w: 20, t: 23},
              i = 14, j = 22, k = 28,
              l = f > 1 ? a * 0.15 : 0,
              n = t * e + l + a * (g[b] + h[m] + i + j + k),
              o = b === 'p' ? 0.75 : m === 't' ? 1.15 : 1;

        document.getElementById('r').innerHTML = `<p>Total: $${(n * o * 1.05).toLocaleString()}</p><p>Per Sqft: $${(n * o * 1.05 / t).toFixed(2)}</p>`;
    }
</script>

<style>
    /* Global styles could be defined here or in a global stylesheet */
    body, * {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .estimator {
        width: 100%;
        max-width: 320px;
        margin: 20px auto;
        padding: 20px;
        background: #fff;
        border-radius: 8px;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
    
    h2 {
        text-align: center;
    }

    label, button, select {
        display: block;
        width: 100%;
        margin: 5px 0;
        padding: 10px;
    }

    button {
        background: #3498db;
        color: white;
        border: none;
        cursor: pointer;
    }

    #r {
        font-size: 1.1em;
        text-align: center;
        margin-top: 20px;
    }
</style>
