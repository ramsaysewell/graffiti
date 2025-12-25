<script>
  let urlCopied = $state(false);
  let commandCopied = $state(false);

  function copyUrl() {
    navigator.clipboard.writeText('https://example.com/share/abc123');
    urlCopied = true;
    setTimeout(() => urlCopied = false, 2000);
  }

  function copyCommand() {
    navigator.clipboard.writeText('npm install graffiti-css');
    commandCopied = true;
    setTimeout(() => commandCopied = false, 2000);
  }
</script>

<div class="stack">
  <!-- Copy URL example -->
  <div class="input-group">
    <input type="text" value="https://example.com/share/abc123" readonly />
    <button onclick={copyUrl}>{urlCopied ? 'Copied!' : 'Copy'}</button>
  </div>

  <!-- Search example with primary button -->
  <div class="input-group">
    <input type="search" placeholder="Search documentation..." />
    <button class="primary">Search</button>
  </div>

  <!-- Command/code snippet with ghost button -->
  <div class="input-group">
    <input type="text" value="npm install graffiti-css" readonly />
    <button class="ghost" onclick={copyCommand}>{commandCopied ? 'Copied!' : 'Copy'}</button>
  </div>

  <!-- Mini variant example -->
  <div class="input-group">
    <input type="text" placeholder="Enter code..." />
    <button class="mini">Apply</button>
  </div>
</div>
