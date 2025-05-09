# Button

Die Button-Komponente der Casoon UI Library bietet verschiedene Stile und Varianten für interaktive Elemente.

## Verwendung

```html
<button class="button button--primary">Primärer Button</button>
<button class="button button--secondary">Sekundärer Button</button>
<button class="button button--outline">Outline Button</button>
```

## Module importieren

```css
@import 'casoon-ui-lib/modules/button.module.css';
```

## Varianten

### Größen

```html
<button class="button button--sm">Kleiner Button</button>
<button class="button">Standard Button</button>
<button class="button button--lg">Großer Button</button>
```

### Zustände

```html
<button class="button" disabled>Deaktivierter Button</button>
<button class="button button--loading">
  <span class="button__text">Ladender Button</span>
  <span class="button__loader"></span>
</button>
```

### Farben

```html
<button class="button button--primary">Primär</button>
<button class="button button--secondary">Sekundär</button>
<button class="button button--success">Erfolg</button>
<button class="button button--danger">Gefahr</button>
<button class="button button--warning">Warnung</button>
<button class="button button--info">Info</button>
```

### Mit Icon

```html
<button class="button button--primary">
  <span class="button__icon">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <path d="M5 12h14"></path>
      <path d="M12 5l7 7-7 7"></path>
    </svg>
  </span>
  <span class="button__text">Mit Icon</span>
</button>
```

### Icon-Button

```html
<button class="button button--icon button--primary">
  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <path d="M12 5v14"></path>
    <path d="M5 12h14"></path>
  </svg>
</button>
```

### Block-Button

```html
<button class="button button--primary button--block">Volle Breite</button>
```

## CSS-Variablen

Die Button-Komponente verwendet folgende CSS-Variablen:

```css
:root {
  --button-padding: 0.5rem 1rem;
  --button-border-radius: 0.25rem;
  --button-font-size: 1rem;
  --button-font-weight: 500;
  --button-transition: all 0.2s ease;
  
  --button-sm-padding: 0.25rem 0.5rem;
  --button-sm-font-size: 0.875rem;
  
  --button-lg-padding: 0.75rem 1.5rem;
  --button-lg-font-size: 1.125rem;
  
  --button-primary-bg: var(--color-primary);
  --button-primary-text: var(--color-white);
  --button-primary-border: var(--color-primary);
  
  --button-secondary-bg: var(--color-secondary);
  --button-secondary-text: var(--color-white);
  --button-secondary-border: var(--color-secondary);
  
  --button-outline-bg: transparent;
  --button-outline-text: var(--color-primary);
  --button-outline-border: var(--color-primary);
  
  --button-success-bg: var(--color-success);
  --button-success-text: var(--color-white);
  --button-success-border: var(--color-success);
  
  --button-danger-bg: var(--color-danger);
  --button-danger-text: var(--color-white);
  --button-danger-border: var(--color-danger);
  
  --button-warning-bg: var(--color-warning);
  --button-warning-text: var(--color-white);
  --button-warning-border: var(--color-warning);
  
  --button-info-bg: var(--color-info);
  --button-info-text: var(--color-white);
  --button-info-border: var(--color-info);
}
```

## Best Practices

### Zugänglichkeit

- Verwenden Sie semantische Button-Elemente (`<button>`) für interaktive Aktionen
- Verwenden Sie Links (`<a>`) für Navigation zu anderen Seiten
- Stellen Sie ausreichenden Kontrast zwischen Text und Hintergrund sicher
- Setzen Sie das `disabled`-Attribut für deaktivierte Buttons
- Vermeiden Sie zu kleine Buttons (mindestens 44x44px Touch-Target)

### Responsive Design

- Verwenden Sie relative Einheiten (rem, em) für Größenangaben
- Passen Sie Padding und Schriftgröße für verschiedene Bildschirmgrößen an
- Verwenden Sie `button--block` auf mobilen Geräten für bessere Touch-Targets

### Performance

- Laden Sie nur die benötigten Button-Varianten
- Vermeiden Sie zu komplexe Schatten oder Animationen auf Buttons

## Integration in Frameworks

### React

```jsx
import 'casoon-ui-lib/core.css';
import 'casoon-ui-lib/themes/day.css';
import 'casoon-ui-lib/modules/button.module.css';

function Button({ 
  children, 
  variant = 'primary',
  size = '',
  block = false,
  isLoading = false,
  ...props 
}) {
  return (
    <button
      className={`button ${variant ? `button--${variant}` : ''} ${size ? `button--${size}` : ''} ${block ? 'button--block' : ''} ${isLoading ? 'button--loading' : ''}`}
      {...props}
    >
      {isLoading && <span className="button__loader"></span>}
      <span className="button__text">{children}</span>
    </button>
  );
}

export default Button;
```

### Vue

```vue
<template>
  <button
    class="button"
    :class="[
      variant ? `button--${variant}` : '',
      size ? `button--${size}` : '',
      { 'button--block': block },
      { 'button--loading': loading }
    ]"
    v-bind="$attrs"
  >
    <span v-if="loading" class="button__loader"></span>
    <span class="button__text">
      <slot></slot>
    </span>
  </button>
</template>

<script>
import 'casoon-ui-lib/core.css';
import 'casoon-ui-lib/themes/day.css';
import 'casoon-ui-lib/modules/button.module.css';

export default {
  name: 'Button',
  props: {
    variant: {
      type: String,
      default: 'primary'
    },
    size: {
      type: String,
      default: ''
    },
    block: {
      type: Boolean,
      default: false
    },
    loading: {
      type: Boolean,
      default: false
    }
  }
}
</script>
```

### Angular

```typescript
// button.component.ts
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-button',
  template: `
    <button
      class="button"
      [class.button--primary]="variant === 'primary'"
      [class.button--secondary]="variant === 'secondary'"
      [class.button--outline]="variant === 'outline'"
      [class.button--success]="variant === 'success'"
      [class.button--danger]="variant === 'danger'"
      [class.button--warning]="variant === 'warning'"
      [class.button--info]="variant === 'info'"
      [class.button--sm]="size === 'sm'"
      [class.button--lg]="size === 'lg'"
      [class.button--block]="block"
      [class.button--loading]="loading"
    >
      <span *ngIf="loading" class="button__loader"></span>
      <span class="button__text">
        <ng-content></ng-content>
      </span>
    </button>
  `
})
export class ButtonComponent {
  @Input() variant: 'primary' | 'secondary' | 'outline' | 'success' | 'danger' | 'warning' | 'info' = 'primary';
  @Input() size: 'sm' | 'lg' | '' = '';
  @Input() block = false;
  @Input() loading = false;
}

// In der styles.css oder angular.json
// @import 'casoon-ui-lib/core.css';
// @import 'casoon-ui-lib/themes/day.css';
// @import 'casoon-ui-lib/modules/button.module.css';
```

### HTML

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="path/to/casoon-ui-lib/core.css">
  <link rel="stylesheet" href="path/to/casoon-ui-lib/themes/day.css">
  <link rel="stylesheet" href="path/to/casoon-ui-lib/modules/button.module.css">
</head>
<body class="theme-day">
  <button class="button button--primary">
    Primärer Button
  </button>
  
  <button class="button button--outline button--lg">
    Großer Outline Button
  </button>
  
  <button class="button button--success button--block">
    Erfolgs-Button mit voller Breite
  </button>
</body>
</html>
``` 