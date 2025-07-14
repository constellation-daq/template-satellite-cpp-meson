# SPDX-FileCopyrightText: 2025 DESY and the Constellation authors
# SPDX-License-Identifier: CC0-1.0

project('Template Satellite',
        ['cpp'],
        version: '0.1',
        license: 'EUPL-1.2',
        default_options: ['warning_level=3', 'cpp_std=c++20'],)

# Setting for Meson template
satellite_type = 'Template'
satellite_sources = files('TemplateSatellite.cpp')
satellite_dependencies = []


satellite_generator = files('generator.cpp')
satellite_main = files('main.cpp')

# Constellation subproject options
constellation_sp_opt = [
  'cxx_tests=disabled',
  'cxx_tools=false',
  'build_gui=none',
]

# Get Constellation dependencies
satellite_dep = dependency('ConstellationSatellite', default_options: constellation_sp_opt)
exec_dep = dependency('ConstellationExec', default_options: constellation_sp_opt)

# Installation directory for satellite
constellation_bindir = exec_dep.get_variable('bindir', default_value: get_option('bindir'))
constellation_libdir = exec_dep.get_variable('libdir', default_value: get_option('libdir'))
satellite_libdir = constellation_libdir / 'ConstellationSatellites'

# Create satellite library
shared_library(
  satellite_type,
  sources: [satellite_generator, satellite_sources],
  dependencies: [satellite_dep] + satellite_dependencies,
  gnu_symbol_visibility: 'hidden',
  install: true,
  install_dir: satellite_libdir,
  install_rpath: constellation_libdir,
)

# Create satellite executable
executable('Satellite' + satellite_type,
  sources: [satellite_main],
  dependencies: [exec_dep],
  install: true,
  install_dir: constellation_bindir,
  install_rpath: constellation_libdir,
)
