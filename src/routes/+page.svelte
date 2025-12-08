<script lang="ts">
  import "$lib/drop-in.css";
  import { swipe_event, scroll_on_load } from "$lib/svelte";
  import ThemeControls from "../docs/ThemeControls.svelte";
  import type { ThemeValues, FontSettings } from "$lib/types";

  let theme_values: ThemeValues = $state({
    fg_light: "#121212",
    fg_dark: "#ffffff",
    bg_light: "#ffffff",
    bg_dark: "#121212",
  });

  let font_settings: FontSettings = $state({
    min_ratio: 6 / 5,
    max_ratio: 4 / 3,
    min_font_size: 14,
    max_font_size: 18,
    min_viewport: 320,
    max_viewport: 1500,
  });

  const colors = [
    "yellow",
    "amber",
    "orange",
    "red",
    "pink",
    "purple",
    "indigo",
    "blue",
    "green",
    "lime",
    "highlighter",
    "brown",
    "teal",
    "gray",
    "slate",
  ];

  const static_colors = [
    { name: "white", note: "Does not change with light/dark mode. Use --fg/--bg for adaptive colors." },
    { name: "black", note: "Does not change with light/dark mode. Use --fg/--bg for adaptive colors." },
  ];

  const scale = [1, 2, 3, 4, 5, 6, 7, 8, 9];
  const scale_with_05 = ["05", 1, 2, 3, 4, 5, 6, 7, 8, 9];

  const theming_scales = [
    { name: "fg", label: "Foreground", note: "Contrasting shades that automatically adapt to light/dark mode. Great for borders, subtle backgrounds, and text emphasis." },
    { name: "bg", label: "Background", note: "Contrasting tints that automatically adapt to light/dark mode. Useful for layered surfaces and subtle overlays." },
  ];

  $effect(() => {
    const temp_root = document.documentElement;
    for (var key in theme_values) {
      temp_root.style.setProperty(
        `--${key.replace("_", "-")}`,
        theme_values[key],
      );
    }
  });
</script>

<svelte:head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Graffiti - A minimal CSS toolkit</title>
</svelte:head>

<ThemeControls bind:theme_values bind:font_settings />

<div
  style="padding: 2rem"
  style:--fg-light={theme_values.fg_light}
  style:--bg-light={theme_values.bg_light}
  style:--fg-dark={theme_values.fg_dark}
  style:--bg-dark={theme_values.bg_dark}
  style:--font-size-min={font_settings.min_font_size}
  style:--font-size-max={font_settings.max_font_size}
  style:--font-ratio-min={font_settings.min_ratio}
  style:--font-ratio-max={font_settings.max_ratio}
  style:--font-width-min={font_settings.min_viewport}
  style:--font-width-max={font_settings.max_viewport}
>
  <style>
    .demo-section {
      margin-block: 3rem;
    }
    .code {
      background: var(--fg-05);
      padding: 1rem;
      border-radius: var(--br-s);
      border: 1px solid var(--fg-1);
    }
    .heading {
      border-bottom: solid 1px;
    }
    h4 {
      font-weight: 400;
    }

    .auto-color {
      padding: var(--pad-m) var(--pad-l);
      border-radius: var(--br-s);
      min-width: 150px;
    }
  </style>

  <header class="header">
    <h1 class="fs-xxl heading" style="margin-top: 0; line-height: 1">
      Graffiti
    </h1>
    <a href="https://github.com/stolinski/graffiti"
      ><svg
        xmlns="http://www.w3.org/2000/svg"
        width="32"
        height="32"
        viewBox="0 0 32 32"
      >
        <title>github</title>
        <g fill="var(--fg)">
          <path
            d="M16,2.345c7.735,0,14,6.265,14,14-.002,6.015-3.839,11.359-9.537,13.282-.7,.14-.963-.298-.963-.665,0-.473,.018-1.978,.018-3.85,0-1.312-.437-2.152-.945-2.59,3.115-.35,6.388-1.54,6.388-6.912,0-1.54-.543-2.783-1.435-3.762,.14-.35,.63-1.785-.14-3.71,0,0-1.173-.385-3.85,1.435-1.12-.315-2.31-.472-3.5-.472s-2.38,.157-3.5,.472c-2.677-1.802-3.85-1.435-3.85-1.435-.77,1.925-.28,3.36-.14,3.71-.892,.98-1.435,2.24-1.435,3.762,0,5.355,3.255,6.563,6.37,6.913-.403,.35-.77,.963-.893,1.872-.805,.368-2.818,.963-4.077-1.155-.263-.42-1.05-1.452-2.152-1.435-1.173,.018-.472,.665,.017,.927,.595,.332,1.277,1.575,1.435,1.978,.28,.787,1.19,2.293,4.707,1.645,0,1.173,.018,2.275,.018,2.607,0,.368-.263,.787-.963,.665-5.719-1.904-9.576-7.255-9.573-13.283,0-7.735,6.265-14,14-14Z"
          ></path>
        </g></svg
      ></a
    >
  </header>

  <main>
    <section
      class="layout-readable center stack"
      style="align-items: center; margin-block-end: 6rem"
    >
      <p>Graffiti is good defaults with some magic tricks</p>
      <h2>Install</h2>
      <p class="code">npm install @drop-in/graffiti</p>
      <p>Then drop in to your project.</p>
      <p class="code">import @drop-in/graffiti</p>
      <p class="fs-xl">or</p>
      <p>
        <a
          class="button"
          href="https://raw.githubusercontent.com/stolinski/graffiti/refs/heads/main/drop-in.css"
          >Just copy and paste from</a
        >
      </p>
      <p>
        <a
          href="https://raw.githubusercontent.com/stolinski/graffiti/refs/heads/main/llms.txt"
          >Give you LLM our docs</a
        >
      </p>
    </section>

    <!-- Typography Demos -->
    <h2 class="heading">Typography</h2>
    <section
      class="demo-section stack"
      style="margin-bottom: var(--vs-xl); --stack-gap: var(--vs-xl)"
    >
      <div>
        <h3>Defaults</h3>
        <h1>H1 - Large Heading</h1>
        <h2>H2 - Med Heading</h2>
        <h3>H3 - Small Heading</h3>
        <h4 style="font-weight: 700">H4 - Xtra Small Heading</h4>
        <h5>H5 - Base Heading</h5>
        <h6>H6 - Small Text Heading</h6>
        <p>
          This is a paragraph of body text. Lorem ipsum dolor sit amet,
          consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
          labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
          exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </p>
      </div>

      <div>
        <h3>Font Size Utilities</h3>
        <p>
          Apply fluid sizing to any element with
          <code>.fs-*</code> classes
        </p>
        <div>
          <p class="fs-xxxl">.fs-xxxl - Triple Extra Large</p>
          <p class="fs-xxl">.fs-xxl - Double Extra Large</p>
          <p class="fs-xl">.fs-xl - Extra Large</p>
          <p class="fs-l">.fs-l - Large</p>
          <p class="fs-m">.fs-m - Medium</p>
          <p class="fs-s">.fs-s - Small</p>
          <p class="fs-base">.fs-base - Base Size</p>
          <p class="fs-xs">.fs-xs - Extra Small</p>
        </div>
      </div>

      <div>
        <h3>Heading Classes</h3>
        <p>
          Apply heading styles to non-heading elements with
          <code>.h1</code> through <code>.h6</code>
        </p>
        <div>
          <p class="h1">This is a p with .h1 class</p>
          <p class="h2">This is a p with .h2 class</p>
          <p class="h3">This is a p with .h3 class</p>
          <p class="h4">This is a p with .h4 class</p>
          <p class="h5">This is a p with .h5 class</p>
          <p class="h6">This is a p with .h6 class</p>
        </div>
      </div>
    </section>

    <!-- Layout Card -->
    <h2 class="heading">Layouts</h2>
    <section class="demo-section stack">
      <h3>.layout-card</h3>
      <p>Auto-fill responsive card grid</p>
      <div class="layout-card" style="background: var(--fg-05)">
        <div class="box">Card 1</div>
        <div class="box">Card 2</div>
        <div class="box">Card 3</div>
        <div class="box">Card 4</div>
      </div>
    </section>

    <!-- Layout Sidebar -->
    <section class="demo-section stack">
      <h3>.layout-sidebar</h3>
      <p>Sidebar + main content (250px default)</p>
      <div class="layout-sidebar" style="background: var(--fg-05)">
        <aside class="box">Sidebar</aside>
        <main class="box">Main Content</main>
      </div>

      <h4>.layout-sidebar.narrow</h4>
      <div class="layout-sidebar narrow" style="background: var(--fg-05)">
        <aside class="box">150px Sidebar</aside>
        <main class="box">Main Content</main>
      </div>

      <h4>.layout-sidebar.wide</h4>
      <div class="layout-sidebar wide" style="background: var(--fg-05)">
        <aside class="box">350px Sidebar</aside>
        <main class="box">Main Content</main>
      </div>

      <h4>.layout-sidebar.invert</h4>
      <div class="layout-sidebar invert" style="background: var(--fg-05)">
        <main class="box">Main Content</main>
        <aside class="box">Sidebar</aside>
      </div>
    </section>

    <!-- Layout Split -->
    <section class="demo-section stack">
      <h3>.layout-split</h3>
      <p>50/50 two column layout</p>
      <div class="layout-split" style="background: var(--fg-05)">
        <div class="box">Left Column</div>
        <div class="box">Right Column</div>
      </div>

      <h4>.layout-split.no-stack</h4>
      <p>Stays side-by-side on mobile</p>
      <div class="layout-split no-stack" style="background: var(--fg-05)">
        <div class="box">Left</div>
        <div class="box">Right</div>
      </div>
    </section>

    <!-- Layout Three Col -->
    <section class="demo-section stack">
      <h3>.layout-three-col</h3>
      <p>Three equal columns</p>
      <div class="layout-three-col" style="background: var(--fg-05)">
        <div class="box">Column 1</div>
        <div class="box">Column 2</div>
        <div class="box">Column 3</div>
      </div>
    </section>

    <!-- Layout Readable -->
    <section class="demo-section stack">
      <h3>.layout-readable</h3>
      <p>Max-width for optimal readability (default: start-aligned)</p>
      <div class="layout-readable" style="background: var(--fg-05)">
        <div class="box">
          <p>
            Learning to drop in on a skateboard is an exciting and challenging
            milestone for any skateboarder. Before attempting to drop in, ensure
            that you have a solid foundation of basic skateboarding skills.
          </p>
        </div>
      </div>

      <h4>.layout-readable.center</h4>
      <div class="layout-readable center" style="background: var(--fg-05)">
        <div class="box">
          <p>Centered readable content with max-width constraint.</p>
        </div>
      </div>

      <h4>.layout-readable.end</h4>
      <div class="layout-readable end" style="background: var(--fg-05)">
        <div class="box">
          <p>End-aligned readable content with max-width constraint.</p>
        </div>
      </div>

      <h4>.layout-readable with .full-bleed child</h4>
      <div
        class="layout-readable center stack"
        style="background: var(--fg-05)"
      >
        <div class="box">
          <p>Regular readable content...</p>
        </div>
        <div class="full-bleed box">
          <p>Full bleed element breaks out of container!</p>
        </div>
        <div class="box">
          <p>More readable content...</p>
        </div>
      </div>

      <h3>.layout-holy-grail</h3>
      <div class="layout-holy-grail" style="background: var(--fg-05)">
        <div class="box">
          <p>Sidebar</p>
        </div>
        <div class="full-bleed box">
          <p>Content</p>
        </div>
        <div class="box">
          <p>Other sidebar</p>
        </div>
      </div>
    </section>

    <!-- Stack -->
    <section class="demo-section">
      <h3>.stack</h3>
      <p>Vertical flexbox stack with gap</p>
      <div class="stack">
        <div class="box">Item 1</div>
        <div class="box">Item 2</div>
        <div class="box">Item 3</div>
      </div>
    </section>

    <!-- Grid Utility -->
    <section class="demo-section">
      <h3>.grid</h3>
      <p>Minimal grid utility (like .flex)</p>
      <div
        class="grid"
        style="grid-template-columns: minmax(auto, 200px) 1fr minmax(auto, 200px)"
      >
        <div class="box">200px</div>
        <div class="box">Flexible</div>
        <div class="box">200px</div>
      </div>
    </section>

    <!-- Cluster Layout -->
    <section class="demo-section stack">
      <h3>.cluster</h3>
      <p>
        Horizontal wrapping list with gap (perfect for tags, pills, breadcrumbs)
      </p>
      <div class="cluster" style="background: var(--fg-05); padding: 1rem">
        <span class="box" style="padding: 0.5rem 1rem">Tag 1</span>
        <span class="box" style="padding: 0.5rem 1rem">Tag 2</span>
        <span class="box" style="padding: 0.5rem 1rem">Tag 3</span>
        <span class="box" style="padding: 0.5rem 1rem">Tag 4</span>
        <span class="box" style="padding: 0.5rem 1rem">Tag 5</span>
        <span class="box" style="padding: 0.5rem 1rem">Tag 6</span>
      </div>
    </section>

    <!-- Carousel Layout -->
    <section class="demo-section stack">
      <h3>.carousel</h3>
      <p>Horizontal scroll with CSS scroll-snap (no JavaScript required)</p>
      <div class="carousel" style="background: var(--fg-05); padding: 1rem">
        <div class="box" style="min-width: 250px; height: 200px">Slide 1</div>
        <div class="box" style="min-width: 250px; height: 200px">Slide 2</div>
        <div class="box" style="min-width: 250px; height: 200px">Slide 3</div>
        <div class="box" style="min-width: 250px; height: 200px">Slide 4</div>
        <div class="box" style="min-width: 250px; height: 200px">Slide 5</div>
      </div>
    </section>

    <section class="demo-section stack">
      <h3>.reel</h3>
      <p>
        Vertical scroll with CSS scroll-snap (customizable height with
        --reel-height)
      </p>
      <div
        class="reel"
        style="background: var(--fg-05); padding: 1rem; --reel-height: 400px;"
      >
        <div class="box" style="min-height: 200px">Panel 1</div>
        <div class="box" style="min-height: 200px">Panel 2</div>
        <div class="box" style="min-height: 200px">Panel 3</div>
        <div class="box" style="min-height: 200px">Panel 4</div>
      </div>
    </section>

    <section class="demo-section stack">
      <h3>.flex</h3>
      <p>Display flex with 20px gap</p>
      <div class="flex" style="background: var(--fg-05); padding: 1rem">
        <div class="box">Flex Item 1</div>
        <div class="box">Flex Item 2</div>
        <div class="box">Flex Item 3</div>
      </div>
    </section>

    <section class="demo-section stack">
      <h3>.split</h3>
      <p>Flex with space-between and top alignment (used in header)</p>
      <div class="split" style="background: var(--fg-05); padding: 1rem">
        <div class="box">Left Side</div>
        <div class="box">Right Side</div>
      </div>
    </section>

    <section class="demo-section stack">
      <h3>.readable</h3>
      <p>Max-width 900px container</p>
      <div class="readable" style="background: var(--fg-05)">
        <div class="box">
          <p>
            This content is constrained to 900px max-width for optimal
            readability. Unlike .layout-readable, this doesn't include padding.
          </p>
        </div>
      </div>
    </section>

    <!-- Elements Section -->
    <h2 class="heading">Elements</h2>
    <section class="demo-section stack">
      <div class="stack">
        <h3>Boxes</h3>
        <div class="layout-card" style="--min-card-width: 200px">
          <div class="box">.box<br />Simple</div>
          <div class="box-glow">.box-glow<br />Subtle</div>
          <div class="box-semi-gloss">
            .box.semi-gloss<br />Semi Gloss
          </div>
          <div class="box-ghost">.box-ghost<br />Simple</div>
          <div style="box-shadow: var(--box), var(--shadow-6)">
            You can make a custom box with CSS variables box-shadow: var(--box),
            var(--shadow-5);
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>.button</h3>
        <p>Button styling for links and non-button elements</p>
        <div class="cluster" style="align-items: center">
          <button>Regular Button</button>
          <a href="/" class="button">Link as Button</a>
          <button class="primary">Primary</button>
          <button class="warning">Warning</button>
          <button class="error">Error</button>
          <button class="success">Success</button>
          <button class="ghost">Ghost</button>
          <button class="mini">Mini Button</button>
        </div>
      </div>

      <div class="stack">
        <h3>Form Validation States</h3>
        <p>Built-in styles for error, success, and warning states</p>

        <form class="stack" style="max-width: 500px">
          <div class="stack" style="--gap: 0.5rem">
            <label for="email-error">Email (error state)</label>
            <input
              type="email"
              id="email-error"
              class="error"
              value="invalid-email"
            />
            <small class="error">Please enter a valid email address</small>
          </div>

          <div class="stack" style="--gap: 0.5rem">
            <label for="username-success">Username (success state)</label>
            <input
              type="text"
              id="username-success"
              class="success"
              value="cool_username"
            />
            <small class="success">Username is available!</small>
          </div>

          <div class="stack" style="--gap: 0.5rem">
            <label for="password-warning">Password (warning state)</label>
            <input
              type="password"
              id="password-warning"
              class="warning"
              value="password123"
            />
            <small class="warning"
              >Password is weak. Consider using a stronger password.</small
            >
          </div>

          <div class="stack" style="--gap: 0.5rem">
            <label for="name-default">Full Name (default state)</label>
            <input
              type="text"
              id="name-default"
              placeholder="Enter your name"
            />
          </div>
        </form>
      </div>

      <div class="stack">
        <h3>.table</h3>
        <p>
          A wrapping div for overflow scrolling, but also generic tables styles
          defined by default without the wrapping claas.
        </p>
        <div class="table">
          <table>
            <thead>
              <tr>
                <th>Hi</th>
                <th>Hello</th>
                <th>sup</th>
                <th>✅ Icon or emoji in this</th>
                <th>Yo</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
              <tr>
                <td>Hi</td>
                <td>Hello</td>
                <td>sup</td>
                <td>
                  Some data in this cell that might be a bit long I don't know.
                </td>
                <td>Yo</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- Components Section -->
    <h2 class="heading">Components</h2>
    <section class="demo-section stack">
      <h3>.header</h3>
      <p>A classic header</p>
      <div class="header">
        <h6>Your Logo</h6>
        <nav>
          <ul>
            <li>
              <a href="/">Home</a>
            </li>
            <li>
              <a href="/">About</a>
            </li>
            <li>
              <a href="/">Contact</a>
            </li>
          </ul>
        </nav>
      </div>
      <h3>.header.border</h3>
      <p>...with subtle border on bottom</p>
      <div class="header border">
        <h6>Your Logo</h6>
        <nav>
          <ul>
            <li>
              <a href="/">Home</a>
            </li>
            <li>
              <a href="/">About</a>
            </li>
            <li>
              <a href="/">Contact</a>
            </li>
          </ul>
        </nav>
      </div>
      <h3>.header.sticky</h3>
      <p>...with subtle border on bottom</p>
      <div style="height: 200px">
        <div class="header border sticky">
          <h6>Your Logo</h6>
          <nav>
            <ul>
              <li>
                <a href="/">Home</a>
              </li>
              <li>
                <a href="/">About</a>
              </li>
              <li>
                <a href="/">Contact</a>
              </li>
            </ul>
          </nav>
        </div>
      </div>

      <h3>.swipe</h3>
      <p>Interactive swipe component</p>
      <div class="swipe" {@attach swipe_event(70, () => {})}>
        <button style="background: var(--red);">❌</button>
        <div style="min-height: 200px">
          <p>
            You can swipe me side to side, no JavaScript. (although you do need
            JS for events)
          </p>
        </div>
        <button style="background: var(--green);">✅</button>
      </div>
      <h3>.swipe.stop</h3>
      <p>Swiper that stays in it's "open" state.</p>
      <div class="swipe stop">
        <button style="background: var(--red);">❌</button>
        <div {@attach scroll_on_load} style="min-height: 100px">
          <p>
            You can swipe me side to side, minor JavaScript needed for Safari.
            (although you do need JS for events)
          </p>
        </div>
        <button style="background: var(--green);">✅</button>
      </div>

      <h3>.swipe.stop.full-bleed</h3>
      <p>Swiper that stays in it's "open" state.</p>
      <div class="swipe stop full-bleed">
        <button style="background: var(--red);">❌</button>
        <div style="min-height: 100px" {@attach scroll_on_load}>
          <p>
            You can swipe me side to side, no JavaScript. (although you do need
            JS for events)
          </p>
        </div>
        <button style="background: var(--green);">✅</button>
      </div>

      <p>You can have multiple buttons of various styles too.</p>
      <div class="swipe stop full-bleed">
        <div class="split even" style="--gap: 10px; padding: var(--pad-m)">
          <button style="height: 100%">Hide</button>
          <button style="height: 100%">Save</button>
        </div>
        <div style="min-height: 100px" {@attach scroll_on_load}>
          <p>
            You can swipe me side to side, no JavaScript. (although you do need
            JS for events)
          </p>
        </div>
        <div class="split even" style="--gap: 10px; padding: var(--pad-m)">
          <button style="height: 100%">Up</button>
          <button style="height: 100%">Down</button>
        </div>
      </div>

      <h3>.callout</h3>
      <p>An informational callout</p>
      <div class="stack">
        <div class="callout">
          <p>.callout This is informational.</p>
        </div>
        <div class="callout warning">
          <p>.callout.warning This is an warning.</p>
        </div>
        <div class="callout error">
          <p>.callout.error This is an error.</p>
        </div>
        <div class="callout success">
          <p>.callout.success This is what success looks like</p>
        </div>

        <div class="callout ghost">
          <p>.callout.ghost This is an generic note.</p>
        </div>
        <div class="callout">
          <h5>You can put anyhting you want..</h5>
          <p>...in this, it's just html, it automatically makes it a "stack"</p>
        </div>
        <div class="callout success">
          <div class="flex">
            <p class="h5">✅</p>
            <div class="stack">
              <h5>a .flex and a div</h5>
              <p>Common UI patterns, just check the soruce</p>
            </div>
          </div>
        </div>
        <div
          class="callout"
          style="--callout-color: var(--pink-1); --callout-border-color: var(--pink-5);"
        >
          <p>
            Custom colors with --callout-color: var(--pink-1);
            --callout-border-color: var(--pink-5);
          </p>
        </div>
        <div class="callout hard">
          <p>Add .hard to any of these for a harder left border</p>
        </div>
      </div>
    </section>

    <!-- Utilities Section -->
    <h2 class="heading">Utilities</h2>
    <section class="demo-section stack">
      <div class="stack">
        <h3>.no-list</h3>
        <p>Remove list styling (margin, padding, list-style)</p>
        <div class="layout-split">
          <div>
            <h4>Regular List</h4>
            <ul>
              <li>Item 1</li>
              <li>Item 2</li>
              <li>Item 3</li>
            </ul>
          </div>
          <div>
            <h4>With .no-list</h4>
            <ul class="no-list">
              <li>Item 1</li>
              <li>Item 2</li>
              <li>Item 3</li>
            </ul>
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>.circle</h3>
        <p>Circular element (default --size: 40px)</p>
        <div class="flex">
          <button class="circle">✓</button>
          <button class="circle" style="--size: 60px">✗</button>
          <button class="circle" style="--size: 80px">!</button>
        </div>
      </div>

      <div class="stack">
        <h3>.row</h3>
        <p>Add vertical margin (--vs-m)</p>
        <div style="background: var(--fg-05); padding: 1rem">
          <div class="box">No .row class</div>
          <div class="box row">With .row class - has margin-block</div>
          <div class="box">No .row class</div>
        </div>
      </div>

      <div class="stack">
        <h3>.visually-hidden</h3>
        <p>Hide element visually but keep accessible to screen readers</p>
        <div class="box">
          <p>
            There is hidden text after this colon:
            <span class="visually-hidden"
              >This text is hidden visually but available to screen readers!</span
            >
          </p>
          <p>You can't see it, but it's there for accessibility.</p>
        </div>
      </div>

      <div class="stack">
        <h3>.fc (Fluid Container)</h3>
        <p>
          Makes typography responsive to container width instead of viewport
        </p>
        <div class="layout-split">
          <div class="box">
            <h4>Regular (viewport-based)</h4>
            <h2>This heading scales with viewport</h2>
            <p>Text scales with viewport width</p>
          </div>
          <div class="box fc">
            <h4>With .fc (container-based)</h4>
            <h2>This heading scales with container</h2>
            <p>Text scales with this box's width</p>
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>Aspect Ratio Utilities</h3>
        <p>
          Maintain specific aspect ratios for containers (useful for images,
          videos, cards)
        </p>
        <div class="layout-card" style="--min-card-width: 200px">
          <div
            class="aspect-square box"
            style="display: grid; place-items: center"
          >
            .aspect-square<br />1:1
          </div>
          <div
            class="aspect-video box"
            style="display: grid; place-items: center"
          >
            .aspect-video<br />16:9
          </div>
          <div
            class="aspect-4-3 box"
            style="display: grid; place-items: center"
          >
            .aspect-4-3<br />4:3
          </div>
          <div
            class="aspect-21-9 box"
            style="display: grid; place-items: center"
          >
            .aspect-21-9<br />21:9
          </div>
        </div>
        <p class="fs-xs">
          Custom: Use <code>aspect-ratio: 2 / 1;</code> or
          <code>aspect-ratio: var(--aspect-ratio);</code>
        </p>
      </div>
    </section>

    <!-- CSS Variables Reference -->
    <section class="demo-section stack">
      <h2 class="heading">CSS Variables Reference</h2>
      <p>
        A big part of Graffiti is the flexible CSS variable system that can be
        used in your CSS to create consistent and adaptable designs.
      </p>

      <div class="stack">
        <h3>Vertical Spacing</h3>
        <div class="layout-card" style="--min-card-width: 150px">
          <div class="box" style="padding: var(--vs-s) var(--vs-s)">
            --vs-s: 0.5rem
          </div>
          <div class="box" style="padding: var(--vs-base) var(--vs-s)">
            --vs-base: 1rem
          </div>
          <div class="box" style="padding: var(--vs-m) var(--vs-s)">
            --vs-m: 1.5rem
          </div>
          <div class="box" style="padding: var(--vs-l) var(--vs-s)">
            --vs-l: 2rem
          </div>
          <div class="box" style="padding: var(--vs-xl) var(--vs-s)">
            --vs-xl: 2rem
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>Border Radius</h3>
        <div class="layout-card" style="--min-card-width: 150px">
          <div class="box" style="border-radius: var(--br-xs)">
            --br-xs: 2px
          </div>
          <div class="box" style="border-radius: var(--br-s)">--br-s: 4px</div>
          <div class="box" style="border-radius: var(--br-m)">--br-m: 8px</div>
          <div class="box" style="border-radius: var(--br-l)">--br-l: 16px</div>
        </div>
      </div>

      <div class="stack">
        <h3>Border</h3>
        <div class="stack">
          <div style="border: var(--border-05)">--border-05</div>
          <div style="border: var(--border-1)">--border-1</div>
          <div style="border: var(--border-2)">--border-2</div>
        </div>
      </div>

      <div class="stack">
        <h3>Padding</h3>
        <div class="layout-card" style="--min-card-width: 150px">
          <div class="box" style="padding: var(--pad-xs)">--pad-xs: 2px</div>
          <div class="box" style="padding: var(--pad-s)">--pad-s: 6px</div>
          <div class="box" style="padding: var(--pad-m)">--pad-m: 12px</div>
          <div class="box" style="padding: var(--pad-l)">--pad-l: 25px</div>
        </div>
      </div>

      <div class="stack">
        <h3>Line Heights</h3>
        <p>Consistent line height tokens for better typography control</p>
        <div class="stack">
          <div class="box" style="line-height: var(--lh-tight)">
            <strong>--lh-tight: 1.2</strong><br />
            This is tight line height, useful for headings and display text where
            you want compact vertical spacing. The quick brown fox jumps over the
            lazy dog.
          </div>
          <div class="box" style="line-height: var(--lh-normal)">
            <strong>--lh-normal: 1.5</strong><br />
            This is normal line height, the default for body text. It provides comfortable
            reading with balanced spacing. The quick brown fox jumps over the lazy
            dog. The five boxing wizards jump quickly.
          </div>
          <div class="box" style="line-height: var(--lh-loose)">
            <strong>--lh-loose: 1.8</strong><br />
            This is loose line height, creating extra vertical breathing room. Useful
            for larger body text or when you want more space between lines. The quick
            brown fox jumps over the lazy dog.
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>Shadows</h3>
        <p>
          Modern layered shadows - subtle in light mode, deeper and more intense
          in dark mode
        </p>
        <div class="layout-card" style="--min-card-width: 200px">
          <div class="box" style="box-shadow: var(--shadow-1)">
            --shadow-1<br />Subtle
          </div>
          <div class="box" style="box-shadow: var(--shadow-2)">
            --shadow-2<br />Light lift
          </div>
          <div class="box" style="box-shadow: var(--shadow-3)">
            --shadow-3<br />Moderate
          </div>
          <div class="box" style="box-shadow: var(--shadow-4)">
            --shadow-4<br />Strong
          </div>
          <div class="box" style="box-shadow: var(--shadow-5)">
            --shadow-5<br />Dramatic
          </div>
          <div class="box" style="box-shadow: var(--shadow-6)">
            --shadow-6<br />Maximum
          </div>
        </div>
      </div>

      <div class="stack">
        <h3>Colors</h3>
        <p>
          OKLCH color system with automatic 1-9 scales generated from base
          colors (scale 5) using relative color syntax
        </p>

        {#each colors as color}
          <div class="stack">
            <h4>{color.charAt(0).toUpperCase() + color.slice(1)} Scale</h4>
            {#if color !== "gray"}
              <div class="auto-color" style="--bg-color: var(--{color})">--{color}</div>
            {/if}
            <div class="cluster">
              {#each scale as n}
                <div class="auto-color" style="--bg-color: var(--{color}-{n})">--{color}-{n}</div>
              {/each}
            </div>
          </div>
        {/each}

        {#each static_colors as { name, note }}
          <div class="stack">
            <h4>{name.charAt(0).toUpperCase() + name.slice(1)} Scale (Static)</h4>
            <p class="fs-xs">{note}</p>
            <div class="auto-color" style="--bg-color: var(--{name})">--{name}</div>
            <div class="cluster">
              {#each scale as n}
                <div class="auto-color" style="--bg-color: var(--{name}-{n})">--{name}-{n}</div>
              {/each}
            </div>
          </div>
        {/each}
      </div>

      <div class="stack">
        <h2 class="heading">Theming Variables</h2>
        <div class="layout-split">
          <div class="box" style="background: var(--fg); color: var(--bg)">
            --fg<br />Foreground color
          </div>
          <div class="box" style="background: var(--bg); color: var(--fg)">
            --bg<br />Background color
          </div>
        </div>
      </div>

      {#each theming_scales as { name, label, note }}
        <div class="stack">
          <h4>{label} Scale</h4>
          <p class="fs-xs">{note}</p>
          <div class="auto-color" style="--bg-color: var(--{name})">--{name}</div>
          <div class="cluster">
            {#each scale_with_05 as n}
              <div class="auto-color" style="--bg-color: var(--{name}-{n})">--{name}-{n}</div>
            {/each}
          </div>
        </div>
      {/each}
    </section>
  </main>

  <footer>
    The website footer. I always hate doing footers for some reason. Just ignore
    this.
  </footer>
</div>
