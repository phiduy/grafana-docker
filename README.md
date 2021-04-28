# [Grafana Panel Plugin](https://grafana.com/tutorials/build-a-panel-plugin/) Guide In A Nutshell With [Docker](https://www.docker.com/)

<!-- [![Build](https://github.com/grafana/grafana-starter-panel/workflows/CI/badge.svg)](https://github.com/grafana/grafana-starter-panel/actions?query=workflow%3A%22CI%22) -->

This guide is only suitable for Grafana 7.0+, Node 14+ and base on [Grafana documentation](https://grafana.com/tutorials/build-a-panel-plugin/). 
> English is my foreign language so if any sentence in my document is not correct. Please let me know <3.
  
### Prerequisites
```
  - Grafana >=7.0
  - NodeJS >=14
  - Docker
  - yarn
```

## What is Grafana Panel Plugin?

Panels are the building blocks of Grafana. They allow you to visualize data in different ways. While Grafana has several types of panels already built-in, you can also build your own panel, to add support for other visualizations.

For more information about panels, refer to the documentation on [Panels](https://grafana.com/docs/grafana/latest/features/panels/panels/)

## Getting started

The easiest way to start developing Grafana plugins is to use the [Grafana Toolkit](https://www.npmjs.com/package/@grafana/toolkit)

### 1. Set up your enviroment
   - Create a directory called grafana-plugins in your preferred workspace. All your plugins must be in this folder.
   - To set up Grafana for plugin development using Docker, run the following command:

   ```bash
    docker run -d -p 3000:3000 -v "$(pwd)"/grafana-plugins:/var/lib/grafana/plugins --name=grafana grafana/grafana:7.0.0
   ```

   - Check your container is ready to go or not

   ```bash
    docker ps
    CONTAINER ID   IMAGE                   COMMAND     CREATED        STATUS       PORTS                    NAMES
    4ebd1f2cd5c3   grafana/grafana:7.0.0   "/run.sh"   16 hours ago   Up 2 hours   0.0.0.0:4000->3000/tcp   grafana
   ```

   - Since Grafana only loads plugins on start-up, you need to restart the container whenever you add or remove a plugin.

   ```bash
    docker restart grafana
   ```
### 2. Create new a plugin

   Tooling for modern web development can be tricky to wrap your head around. While you certainly can write your own webpack configuration, for this guide, you’ll be using grafana-toolkit.

   [grafana-toolkit](https://github.com/grafana/grafana/tree/master/packages/grafana-toolkit) is a CLI application that simplifies Grafana plugin development, so that you can focus on code. The toolkit takes care of building and testing for you.

   **Create your plugin as subfolder in ```grafana-plugins``` folder**

   - In the plugin directory, create a plugin from template using the plugin:create command:

     ```bash
     cd grafana-plugins
     npx @grafana/toolkit plugin:create my-plugin
     ```

   - Change directory.
     
     ```bash
     cd my-plugin
     ```

   - Download necessary dependencies:

     ```bash
     yarn install
     ```

### 3. Development and build plugin 
   
   **Go to directory of your plugin**

   - Development mode or run in watch mode

     ```bash
     yarn dev
     ```
     or
     ```bash
     yarn watch
     ```

   - Production mode

     ```bash
     yarn build
     ```

### 5. Restart the Grafana server for Grafana to discover your plugin.

   ```bash
   docker restart `your-grafana-container-name`
   ```

### 6. Open Grafana and go to **Configuration -> Plugins**. Make sure that your plugin is there.

## Learn more

- [Build a panel plugin tutorial](https://grafana.com/tutorials/build-a-panel-plugin)
- [Grafana documentation](https://grafana.com/docs/)
- [Grafana Tutorials](https://grafana.com/tutorials/) - Grafana Tutorials are step-by-step guides that help you make the most of Grafana
- [Grafana UI Library](https://developers.grafana.com/ui) - UI components to help you build interfaces using Grafana Design System

## Contributing
[Me](https://github.com/phiduy) and my big bro [songhanpoo](https://github.com/songhanpoo)
