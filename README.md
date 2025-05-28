# react-migration-guide- 18 to 19

Here's a **complete, detailed migration guide** from **React 18 to React 19**, including setup, breaking changes, new features, compiler integration, and ecosystem updates.

---

## 🧭 1. Upgrade Core Packages

Update to React 19 and ReactDOM 19:

```bash
npm install react@19 react-dom@19
```

If you're using experimental features:

```bash
npm install react@experimental react-dom@experimental
```

---

## 🔄 2. Breaking Changes

### ✅ a. `defaultProps` on Function Components Removed

```tsx
// ❌ This no longer works:
function Button(props) {}
Button.defaultProps = { color: 'blue' };

// ✅ Use default values instead:
function Button({ color = 'blue' }) {}
```

---

### ✅ b. Legacy Context API Removed

Old context using `getChildContext` and `childContextTypes` is no longer supported. Migrate to the modern Context API.

---

### ✅ c. `ReactDOM.render` Deprecated

Ensure you're using `createRoot` introduced in React 18:

```tsx
import { createRoot } from 'react-dom/client';
createRoot(document.getElementById('root')!).render(<App />);
```

---

## ⚡ 3. New Features in React 19

### 🔹 a. React Compiler (RC)

Automatically memoizes your components during build-time.

Install and configure:

```bash
npm install --save-dev --save-exact babel-plugin-react-compiler@rc
```

`.babelrc`:

```json
{
  "plugins": ["react-compiler"]
}
```

React Compiler will:

* Automatically add `memo`/`useMemo`
* Optimize re-renders
* Works with SWC and Babel (OXC support coming)

---

### 🔹 b. View Transitions API *(Experimental)*

Smooth transitions between routes/pages.

Usage with React Router:

```tsx
import { startViewTransition } from 'react';

startViewTransition(() => {
  navigate('/about');
});
```

---

### 🔹 c. `Activity` API *(Experimental)*

Tracks user activity to pause/resume effects, fetches, or renders based on app visibility or user input.

---

### 🔹 d. Fragment Refs

Refs now work on `<></>` fragments.

```tsx
const ref = useRef();
return <><div ref={ref}>Hello</div></>;
```

---

### 🔹 e. Automatic Effect Dependency Tracking *(Experimental)*

Detects missing dependencies in `useEffect`, auto-infers dependencies with the compiler.

---

### 🔹 f. Concurrent Stores

New mechanism for handling concurrent updates in global stores more efficiently.

---

## 🧩 4. Ecosystem Changes

### 🔸 a. `eslint-plugin-react-compiler` merged into `eslint-plugin-react-hooks`

Update to the latest version:

```bash
npm install eslint-plugin-react-hooks@latest
```

---

### 🔸 b. `eslint-config-react-app` (if using CRA)

May need manual patching or overrides until officially updated for React 19.

---

## 🧪 5. Testing & Validation

* ✅ Run all unit/integration tests
* ✅ Test hydration in SSR/Next.js apps
* ✅ Check for any unexpected unmount/remount from StrictMode
* ✅ Test forms, refs, memoization
* ✅ Watch for console warnings or build errors (compiler feedback)

---

## 🧱 6. Optional: Opt-In Experimental Setup

```bash
npm install react@experimental react-dom@experimental
```

Useful for:

* Trying Fragment Refs
* Activity API
* View Transitions

---

## 📁 7. Suggested File Updates

### `package.json`

```json
{
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "babel-plugin-react-compiler": "^19.0.0-rc",
    "eslint-plugin-react-hooks": "^4.6.0"
  }
}
```

### `.babelrc`

```json
{
  "presets": ["@babel/preset-react"],
  "plugins": ["react-compiler"]
}
```

---

## 📝 Final Advice

* **Use the Compiler** only if your build system supports it (Vite, SWC, Babel).
* Migrate in stages for large apps (start with core packages and add compiler later).
* Monitor React [release blog](https://react.dev/blog) and [React Compiler updates](https://react.dev/blog/2025/04/21/react-compiler-rc) for upcoming stable changes.

---

Here's a **complete, detailed migration guide** from **React 18 to React 19**, including setup, breaking changes, new features, compiler integration, and ecosystem updates.

---

## 🧭 1. Upgrade Core Packages

Update to React 19 and ReactDOM 19:

```bash
npm install react@19 react-dom@19
```

If you're using experimental features:

```bash
npm install react@experimental react-dom@experimental
```

---

## 🔄 2. Breaking Changes

### ✅ a. `defaultProps` on Function Components Removed

```tsx
// ❌ This no longer works:
function Button(props) {}
Button.defaultProps = { color: 'blue' };

// ✅ Use default values instead:
function Button({ color = 'blue' }) {}
```

---

### ✅ b. Legacy Context API Removed

Old context using `getChildContext` and `childContextTypes` is no longer supported. Migrate to the modern Context API.

---

### ✅ c. `ReactDOM.render` Deprecated

Ensure you're using `createRoot` introduced in React 18:

```tsx
import { createRoot } from 'react-dom/client';
createRoot(document.getElementById('root')!).render(<App />);
```

---

## ⚡ 3. New Features in React 19

### 🔹 a. React Compiler (RC)

Automatically memoizes your components during build-time.

Install and configure:

```bash
npm install --save-dev --save-exact babel-plugin-react-compiler@rc
```

`.babelrc`:

```json
{
  "plugins": ["react-compiler"]
}
```

React Compiler will:

* Automatically add `memo`/`useMemo`
* Optimize re-renders
* Works with SWC and Babel (OXC support coming)

---

### 🔹 b. View Transitions API *(Experimental)*

Smooth transitions between routes/pages.

Usage with React Router:

```tsx
import { startViewTransition } from 'react';

startViewTransition(() => {
  navigate('/about');
});
```

---

### 🔹 c. `Activity` API *(Experimental)*

Tracks user activity to pause/resume effects, fetches, or renders based on app visibility or user input.

---

### 🔹 d. Fragment Refs

Refs now work on `<></>` fragments.

```tsx
const ref = useRef();
return <><div ref={ref}>Hello</div></>;
```

---

### 🔹 e. Automatic Effect Dependency Tracking *(Experimental)*

Detects missing dependencies in `useEffect`, auto-infers dependencies with the compiler.

---

### 🔹 f. Concurrent Stores

New mechanism for handling concurrent updates in global stores more efficiently.

---

## 🧩 4. Ecosystem Changes

### 🔸 a. `eslint-plugin-react-compiler` merged into `eslint-plugin-react-hooks`

Update to the latest version:

```bash
npm install eslint-plugin-react-hooks@latest
```

---

### 🔸 b. `eslint-config-react-app` (if using CRA)

May need manual patching or overrides until officially updated for React 19.

---

## 🧪 5. Testing & Validation

* ✅ Run all unit/integration tests
* ✅ Test hydration in SSR/Next.js apps
* ✅ Check for any unexpected unmount/remount from StrictMode
* ✅ Test forms, refs, memoization
* ✅ Watch for console warnings or build errors (compiler feedback)

---

## 🧱 6. Optional: Opt-In Experimental Setup

```bash
npm install react@experimental react-dom@experimental
```

Useful for:

* Trying Fragment Refs
* Activity API
* View Transitions

---

## 📁 7. Suggested File Updates

### `package.json`

```json
{
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "babel-plugin-react-compiler": "^19.0.0-rc",
    "eslint-plugin-react-hooks": "^4.6.0"
  }
}
```

### `.babelrc`

```json
{
  "presets": ["@babel/preset-react"],
  "plugins": ["react-compiler"]
}
```

---

## 📝 Final Advice

* **Use the Compiler** only if your build system supports it (Vite, SWC, Babel).
* Migrate in stages for large apps (start with core packages and add compiler later).
* Monitor React [release blog](https://react.dev/blog) and [React Compiler updates](https://react.dev/blog/2025/04/21/react-compiler-rc) for upcoming stable changes.

---

Here are the **file-level updates** needed for migrating from **React 18 to React 19**, including changes for core setup, ESLint, Babel (React Compiler), and optional experimental features.

---

### 📁 1. `package.json`

Update dependencies:

```json
{
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "babel-plugin-react-compiler": "^0.2.0-rc",         // optional
    "eslint-plugin-react-hooks": "^4.6.0"
  }
}
```

For experimental features:

```bash
npm install react@experimental react-dom@experimental
```

---

### 📁 2. `.babelrc` or `babel.config.js`

If using Babel, add the compiler plugin:

```json
{
  "presets": ["@babel/preset-react"],
  "plugins": ["react-compiler"]
}
```

If using Vite/SWC — no need for `.babelrc`. Instead, configure `vite.config.ts` with SWC plugin support if available.

---

### 📁 3. `vite.config.ts` (if using Vite)

Ensure React plugin and compiler is applied:

```ts
import react from '@vitejs/plugin-react';
export default {
  plugins: [react()],
};
```

---

### 📁 4. `.eslintrc.js`

Update ESLint config:

```js
module.exports = {
  plugins: ['react-hooks'],
  rules: {
    'react-hooks/rules-of-hooks': 'error',
    'react-hooks/exhaustive-deps': 'warn'
  }
};
```

Remove `eslint-plugin-react-compiler` if used previously.

---

### 📁 5. `index.tsx` / `main.tsx`

Ensure you’re using the `createRoot` API:

```tsx
import React from 'react';
import { createRoot } from 'react-dom/client';
import App from './App';

const container = document.getElementById('root');
const root = createRoot(container!);
root.render(<App />);
```

---

### 📁 6. `tsconfig.json` (Optional SWC/Babel-Free Support)

If using SWC + experimental compiler:

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "jsx": "react-jsx"
  }
}
```

---

