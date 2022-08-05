# Popup

[component-header:sl-popup]

A description of the component goes here.

```html preview
<div class="popup-overview">
  <sl-popup placement="top" active>
    <span slot="anchor">This is the anchor</span>
    <div class="box"></div>
  </sl-popup>
</div>

<div class="popup-overview-options">
  <sl-select label="Placement" name="placement" value="top" class="popup-overview-select">
    <sl-menu-item value="top">top</sl-menu-item>
    <sl-menu-item value="top-start">top-start</sl-menu-item>
    <sl-menu-item value="top-end">top-end</sl-menu-item>
    <sl-menu-item value="bottom">bottom</sl-menu-item>
    <sl-menu-item value="bottom-start">bottom-start</sl-menu-item>
    <sl-menu-item value="bottom-end">bottom-end</sl-menu-item>
    <sl-menu-item value="right">right</sl-menu-item>
    <sl-menu-item value="right-start">right-start</sl-menu-item>
    <sl-menu-item value="right-end">right-end</sl-menu-item>
    <sl-menu-item value="left">left</sl-menu-item>
    <sl-menu-item value="left-start">left-start</sl-menu-item>
    <sl-menu-item value="left-end">left-end</sl-menu-item>
  </sl-select>
  <sl-input type="number" name="distance" label="distance" value="0"></sl-input>
  <sl-input type="number" name="skidding" label="Skidding" value="0"></sl-input>
  <sl-switch name="active" checked>Active</sl-switch>
  <sl-switch name="arrow">Arrow</sl-switch>
  <sl-switch name="fixed">Fixed</sl-switch>
</div>

<script>
  const container = document.querySelector('.popup-overview');
  const popup = container.querySelector('sl-popup');
  const options = document.querySelector('.popup-overview-options');
  const select = options.querySelector('sl-select[name="placement"]');
  const distance = options.querySelector('sl-input[name="distance"]');
  const skidding = options.querySelector('sl-input[name="skidding"]');
  const active = options.querySelector('sl-switch[name="active"]');
  const arrow = options.querySelector('sl-switch[name="arrow"]');
  const fixed = options.querySelector('sl-switch[name="fixed"]');

  select.addEventListener('sl-change', () => (popup.placement = select.value));
  distance.addEventListener('sl-input', () => (popup.distance = distance.value));
  skidding.addEventListener('sl-input', () => (popup.skidding = skidding.value));
  active.addEventListener('sl-change', () => (popup.active = active.checked));
  arrow.addEventListener('sl-change', () => (popup.arrow = arrow.checked));
  fixed.addEventListener('sl-change', () => (popup.strategy = fixed.checked ? 'fixed' : 'absolute'));
</script>

<style>
  .popup-overview {
    padding: calc(50px + 1rem);
  }

  .popup-overview sl-popup {
    --arrow-color: var(--sl-color-primary-600);
    --arrow-size: 4px;
  }

  .popup-overview [slot='anchor'] {
    border: dashed 2px var(--sl-color-neutral-200);
    padding: 0.5rem;
  }

  .popup-overview .box {
    width: 50px;
    height: 50px;
    background: var(--sl-color-primary-600);
  }

  .popup-overview-options {
    display: flex;
    flex-wrap: wrap;
    align-items: end;
    gap: 1rem;
  }

  .popup-overview-options sl-select {
    width: 160px;
  }

  .popup-overview-options sl-input {
    width: 100px;
  }

  .popup-overview-options + .popup-overview-options {
    margin-top: 1rem;
  }
</style>
```

## Examples

### Fixed Positioning Strategy

By default, an absolute positioning strategy is used for maximum performance. However, if your content is within a container that has `overflow: auto|hidden` the popup will be clipped. To work around this, you can switch to the fixed positioning strategy by setting the `strategy` attribute to `fixed`.

The fixed positioning strategy allows the content to break out containers that clip them. When using this strategy, it's important to note that the content will be positioned _relative to its containing block_, which is usually the viewport unless an ancestor uses a `transform`, `perspective`, or `filter`. [Refer to this page](https://developer.mozilla.org/en-US/docs/Web/CSS/position#fixed) for more details.

TODO

### Arrows

TODO

[component-metadata:sl-popup]