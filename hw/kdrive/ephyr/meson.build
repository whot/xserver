srcs = [
    'ephyr.c',
    'ephyrinit.c',
    'ephyrcursor.c',
    'ephyr_draw.c',
    'hostx.c',
    'os.c',
]

xephyr_dep = [
    common_dep,
    dependency('xcb'),
    dependency('xcb-shape'),
    dependency('xcb-render'),
    dependency('xcb-renderutil'),
    dependency('xcb-aux'),
    dependency('xcb-image'),
    dependency('xcb-icccm'),
    dependency('xcb-shm'),
    dependency('xcb-keysyms'),
    dependency('xcb-randr'),
    dependency('xcb-xkb'),
]

xephyr_glamor = []
if build_glamor
    srcs += 'ephyr_glamor_glx.c'
    if build_xv
        srcs += 'ephyr_glamor_xv.c'
    endif
    xephyr_glamor += glamor
    xephyr_glamor += glamor_egl_stubs
    xephyr_dep += dependency('x11-xcb')
endif

if build_xv
    srcs += 'ephyrvideo.c'
    xephyr_dep += dependency('xcb-xv')
endif

executable(
    'Xephyr',
    srcs,
    include_directories: [
        inc,
        include_directories('../src')
    ],
    dependencies: xephyr_dep,
    link_with: [
        libxserver_main,
        libxserver_exa,
        xephyr_glamor,
        kdrive,
        libxserver_fb,
        libxserver,
        libxserver_config,
        libxserver_xkb_stubs,
        libxserver_xi_stubs,
        libxserver_glx,
    ],
    install: true,
)
