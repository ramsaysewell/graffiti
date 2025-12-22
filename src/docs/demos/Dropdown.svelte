<div class="cluster">
  <!-- Basic dropdown with header, items, and dividers -->
  <div class="dropdown" style="--anchor: --dropdown-options">
    <button popovertarget="dropdown-options">Options</button>
    <div id="dropdown-options" popover class="dropdown-menu">
      <div class="dropdown-header">Account</div>
      <hr>
      <a href="#profile">Profile</a>
      <a href="#settings">Settings</a>
      <hr>
      <button>Sign Out</button>
    </div>
  </div>

  <!-- End-aligned dropdown -->
  <div class="dropdown end" style="--anchor: --dropdown-actions">
    <button popovertarget="dropdown-actions">Actions</button>
    <div id="dropdown-actions" popover class="dropdown-menu">
      <div class="dropdown-header">Quick Actions</div>
      <hr>
      <a href="#edit">Edit</a>
      <a href="#duplicate">Duplicate</a>
      <a href="#archive">Archive</a>
      <hr>
      <button>Delete</button>
    </div>
  </div>
</div>
