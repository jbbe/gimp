subdir('images')

plugin_name = 'lighting'

plugin_sources = [
  'lighting-apply.c',
  'lighting-icons.c',
  'lighting-image.c',
  'lighting-main.c',
  'lighting-preview.c',
  'lighting-shade.c',
  'lighting-ui.c',
  lighting_icon_sources,
]

if platform_windows
  plugin_sources += windows.compile_resources(
    gimp_plugins_rc,
    args: [
      '--define', 'ORIGINALFILENAME_STR="@0@"'.format(plugin_name+'.exe'),
      '--define', 'INTERNALNAME_STR="@0@"'    .format(plugin_name),
      '--define', 'TOP_SRCDIR="@0@"'          .format(meson.source_root()),
    ],
    include_directories: [
      rootInclude, appInclude,
    ],
  )
endif

executable(plugin_name,
  plugin_sources,
  include_directories: [ rootInclude, include_directories('.'), ],
  dependencies: [
    gtk3, gegl, math,
  ],
  link_with: [
    libgimp,
    libgimpbase,
    libgimpcolor,
    libgimpconfig,
    libgimpmath,
    libgimpui,
    libgimpwidgets,
  ],
  install: true,
  install_dir: gimpplugindir / 'plug-ins' / plugin_name,
)
