# Elixir Phoenix with Dart Sass
Docker image suitable for local development and compiling Elixir applications for ARM64 architecture.
Tested with docker-in-docker CI for GitLab.

## Configuration and usage
There is a Dart Sass library for Elixir Phoenix:
https://github.com/CargoSense/dart_sass

It doesn't support precompiled Dart/Sass unless it is directly downloaded from the main branch.
In your mix.exs add:
```elixir
{:dart_sass, git: "https://github.com/CargoSense/dart_sass", runtime: Mix.env() == :dev}
```
in the config.exs, specify paths for the Dart and Sass as environment variables:

```elixir
config :dart_sass,
  sass_path: System.get_env("MIX_SASS_PATH"),
  dart_path: System.get_env("MIX_SASS_DART_PATH"),
```

You can preview dart and sass location using these commands:
- `which dart`
- `which sass`

As for the latest version of this image, these are default locations where sass and dart are installed:
- /root/.pub-cache/bin/sass
- /usr/lib/dart/bin/dart
