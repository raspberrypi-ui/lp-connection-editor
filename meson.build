project ('lp-connection-editor','c',
  default_options: [
    'c_std=gnu99'
  ],
)

prefix = get_option('prefix')
share_dir = join_paths(prefix, 'share')
resource_dir = join_paths(share_dir, meson.project_name())
desktop_dir = join_paths(share_dir, 'applications')
locale_dir = join_paths(prefix, get_option('localedir'))

i18n = import('i18n')

config_h = configuration_data()

config_h.set_quoted('GETTEXT_PACKAGE', meson.project_name())
config_h.set_quoted('VERSION', meson.project_version())
config_h.set10('WITH_SELINUX', true)
config_h.set10('WITH_JANSSON', true)

if not meson.get_compiler('c').has_type('pid_t', prefix: '#include<sys/types.h>')
  config_h.set('pid_t', 'int')
endif

config = 'config.h'

configure_file(
  input: config + '.meson',
  output: config,
  configuration: config_h
)

add_project_arguments('-DPACKAGE_LOCALE_DIR="' + share_dir + '/locale"', language : 'c' )

subdir('po')
subdir('src')
subdir('data')
