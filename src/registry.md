The asterai registry is where components are published and discovered. Think of it as npm for AI agent tools—but language-agnostic.

## Namespaces

Every user has a namespace matching their username. When you publish a component, it's scoped to your namespace:

```
your-username:component-name@1.0.0
```

## Public Components

Public components are free to publish and use. Anyone can discover and import them into their environments.

Browse available components at [asterai.io/registry](https://asterai.io/registry).

## Private Components

Private components are only visible to you and your team. Use them for proprietary tools or internal integrations.

## Publishing

Publish a component with the CLI:

```bash
asterai publish
```

The component version is defined in your `component.wit` file. Each version is immutable—once published, it cannot be modified or overwritten.

## Using Components

Add a component to your environment through the console or by importing it in your component's WIT file:

```wit
package your-username:my-component@0.1.0;

world component {
  import other-user:useful-tool/api@1.0.0;

  export my-function: func() -> string;
}
```

## Versioning

Components follow [semantic versioning](https://semver.org/):

- **Major** (1.x.x): Breaking changes
- **Minor** (x.1.x): New features, backwards compatible
- **Patch** (x.x.1): Bug fixes, backwards compatible

Choose your dependency versions carefully. Pinning to exact versions ensures reproducibility; using ranges allows automatic updates.
