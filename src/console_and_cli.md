## CLI

The asterai CLI is the primary tool for building, publishing, and running components and environments.

### Installation

```bash
npm install -g @asterai/cli
```

### Authentication

```bash
asterai auth login <api-key>    # Authenticate to the registry
asterai auth logout             # Clear authentication
asterai auth status             # Show current auth status
```

### Component Commands

```bash
asterai component init <name>   # Create a new component project
asterai component push          # Push component to the registry (from project dir)
asterai component pull <name>   # Pull a component from the registry
asterai component list          # List your components
asterai component pkg           # Package the component's WIT into a WASM package
```

### Environment Commands

```bash
asterai env init <name>                           # Create a new environment
asterai env run <name>                            # Run environment locally
asterai env call <name> <component> <fn> [args]   # Call a function
asterai env push <name>                           # Push environment to registry
asterai env pull <name>                           # Pull environment from registry
asterai env list                                  # List your environments
asterai env inspect <name>                        # Show environment details
asterai env add <name> --component <spec>         # Add a component
asterai env remove <name> --component <spec>      # Remove a component
asterai env set-var <name> --var NAME=VALUE       # Set environment variable
```

## Cloud Console

The [cloud console](https://asterai.io/dashboard) provides a web interface for managing your asterai resources:

- **Environments**: Create, configure, and monitor environments
- **Components**: View your published components and their versions
- **Secrets**: Manage environment variables and API keys
- **Usage**: Track execution metrics and costs

## Next Steps

- [Hello World guide](/src/hello_world): Build and run your first component
- [Components](/src/components): Learn how components work
