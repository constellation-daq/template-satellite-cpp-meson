---
# SPDX-FileCopyrightText: 2025 DESY and the Constellation authors
# SPDX-License-Identifier: CC-BY-4.0 OR EUPL-1.2
title: "Template"
description: "Template satellite serving as the basis for new developments"
category: "Example Templates"
---

## First Steps

* Rename the satellite using the self-destructing script:

  ```sh
  $ rename-template.py MyName
  ```

* Implement the satellite code
* Build the satellite:

  ```sh
  $ meson setup build/
  $ meson compile -C build/
  ```

* Update this README
  * Remove the "First Steps" section
  * Update the satellite description, parameter and metric list, custom commands
  * Add a configuration example for easy copy & paste

## Description

This is a detailed description of the satellite and its functionality.
Possible dependencies are described alongside its features, potential pitfalls and other information.

## Parameters

The following parameters are read and interpreted by this satellite. Parameters without a default value are required.

| Parameter  | Description | Type | Default Value |
|------------|-------------|------|---------------|
| `example` | Description of the parameter | Boolean | `true` |

### Configuration Example

An example configuration for this satellite which could be dropped into a Constellation configuration as a starting point

```toml
[Template.One]
example = false
```

## Metrics

The following metrics are distributed by this satellite and can be subscribed to.

| Metric | Description | Value Type | Metric Type | Interval |
|--------|-------------|------------|-------------|----------|
| `TIME` | Time since launch in seconds | Float | `LAST_VALUE` | 10s |

## Custom Commands

This section describes all custom commands the satellite exposes to the command interface.

| Command | Description | Arguments | Return Value | Allowed States |
|---------|-------------|-----------|--------------|----------------|
| `test` | This command always returns `true` | - | Boolean, always `true` | `NEW`, `INIT`, `ORBIT` |
