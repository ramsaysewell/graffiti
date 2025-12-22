<!-- App Shell Layout Demo -->
<!-- Uses .layout-sidebar.fill for sticky full-height sidebar -->
<!-- Uses .split.vertical for sidebar internal layout (nav top, footer bottom) -->

<div class="layout-sidebar fill" style="--layout-gap: 0; height: 400px;">
  <aside class="split vertical box">
    <nav class="sidebar-nav">
      <strong style="padding: var(--pad-s) var(--pad-m);">APP NAME</strong>
      <a href="#home" class="active">
        <svg viewBox="0 0 20 20" fill="currentColor"><path d="M10 2L3 9h2v8h4v-5h2v5h4V9h2L10 2z"/></svg>
        Home
      </a>
      <a href="#dashboard">
        <svg viewBox="0 0 20 20" fill="currentColor"><path d="M3 3h6v8H3V3zm8 0h6v4h-6V3zm0 6h6v8h-6V9zM3 13h6v4H3v-4z"/></svg>
        Dashboard
      </a>
      <details>
        <summary>
          <svg viewBox="0 0 20 20" fill="currentColor"><path d="M10 13a3 3 0 100-6 3 3 0 000 6z"/><path fill-rule="evenodd" d="M10 2a1 1 0 011 1v1.07a6.97 6.97 0 012.5 1.03l.76-.76a1 1 0 111.41 1.41l-.76.76A6.97 6.97 0 0116.93 9H18a1 1 0 110 2h-1.07a6.97 6.97 0 01-1.03 2.5l.76.76a1 1 0 11-1.41 1.41l-.76-.76a6.97 6.97 0 01-2.5 1.03V18a1 1 0 11-2 0v-1.07a6.97 6.97 0 01-2.5-1.03l-.76.76a1 1 0 11-1.41-1.41l.76-.76A6.97 6.97 0 013.07 11H2a1 1 0 110-2h1.07a6.97 6.97 0 011.03-2.5l-.76-.76a1 1 0 111.41-1.41l.76.76A6.97 6.97 0 019 3.07V2a1 1 0 011-1z" clip-rule="evenodd"/></svg>
          Settings
        </summary>
        <a href="#general">General</a>
        <a href="#security">Security</a>
        <a href="#billing">Billing</a>
      </details>
    </nav>
    <div class="stack" style="padding: var(--pad-s) var(--pad-m);">
      <small>v1.0.0</small>
      <button class="mini">Upgrade</button>
    </div>
  </aside>
  <section class="stack" style="padding: var(--pad-l);">
    <h3>Main Content</h3>
    <p>The sidebar stays fixed while this content scrolls independently.</p>
    <div class="box">Content block 1</div>
  </section>
</div>
