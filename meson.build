project(
    'ibm-ups',
    'cpp',
    default_options: [
        'warning_level=3',
        'werror=true',
        'cpp_std=c++23',
        'buildtype=debugoptimized',
        'prefix=/usr'
    ],
    license: 'Apache-2.0',
    version: '1.0',
    meson_version: '>=1.1.1',
)

phosphor_dbus_interfaces = dependency('phosphor-dbus-interfaces')
phosphor_logging = dependency('phosphor-logging')
sdbusplus = dependency('sdbusplus')
sdeventplus = dependency('sdeventplus')
stdplus = dependency('stdplus')

cxx = meson.get_compiler('cpp')
if cxx.has_header('CLI/CLI.hpp')
    cli11_dep = declare_dependency()
else
    cli11_dep = dependency('CLI11')
endif

systemd = dependency('systemd')
servicedir = systemd.get_variable('systemdsystemunitdir')
fs = import('fs')
fs.copyfile('ibm-ups.service', install: true, install_dir: servicedir)

ibm_ups = executable(
    'ibm-ups',
    'error_logging.cpp',
    'main.cpp',
    'monitor.cpp',
    'ups.cpp',
    dependencies: [
        phosphor_dbus_interfaces,
        phosphor_logging,
        sdbusplus,
        sdeventplus,
        stdplus
    ],
    install: true
)
