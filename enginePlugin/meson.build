# version 2 also compiled a C-language plugin: resynthesizer-gui
# Since 2023 replaced by a ScriptFu plugin.
# Since 2023 we obsolete the C-language control panel plugin because
# 1) uses obsolete Gtk-2
# 2) is non-declarative


plugin_name = 'resynthesizer'
# assert defined earlier: gimpplugindir = '/usr/local/lib/x86_64-linux-gnu/gimp/2.99'

# !!! Other .h files have compilable code (they are not just headers)
# but we only need to list the top compiled files.

resynthesizer_sources = [
  'plugin.c',     # main for a plugin
  'resynthesizer.c',
  'debug.c',
  'pluginParams.c',
  'drawable.c',
]


# define dependencies on libraries

# libgimp, the API to gimp.
# Need headers i.e. include file libgimp.h
# If fails, try install a dev package such as "gimp-3.0-dev"
# version 2.99 is the beta for v3.0
gimp_dep = dependency('gimp-3.0', version : '>=2.99.0')

# resynthesizer engine plugin calls (depends on)
# the resynthesizer engine library (libresynthesizer).
# Which we also first build.
# That dependency on libresynthesizer is declared below, see links_with


# Since 3.0 a plugin must install to a dir named the same as the plugin
# Hence: install_dir: ...

# Summarizing dependency: libgimp and libresynthesizer

executable(plugin_name,
  resynthesizer_sources,
  dependencies: [
    gimp_dep,
  ],
  c_args: [ '-DG_LOG_DOMAIN="Resynthesizer"', '-DGIMP_COMPILATION', ],
  link_with : [
    resynth_lib,
  ],
  include_directories: resynthesizer_inc,
  install: true,
  install_dir: gimpplugindir / plugin_name,
)
