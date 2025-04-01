sources = files(
  'ce-page.c',
  'ce-polkit-button.c',
  'ce-polkit.c',
  'ce-utils.c',
  'connection-helpers.c',
  'ip4-routes-dialog.c',
  'ip6-routes-dialog.c',
  'nm-connection-editor.c',
  'nm-connection-list.c',
  'main.c',
  'page-8021x-security.c',
  'page-bridge.c',
  'page-bridge-port.c',
  'page-bluetooth.c',
  'page-bond.c',
  'page-dcb.c',
  'page-dsl.c',
  'page-ethernet.c',
  'page-general.c',
  'page-infiniband.c',
  'page-ip-tunnel.c',
  'page-ip4.c',
  'page-ip6.c',
  'page-macsec.c',
  'page-controller.c',
  'page-mobile.c',
  'page-ppp.c',
  'page-proxy.c',
  'page-team.c',
  'page-team-port.c',
  'page-vlan.c',
  'page-vpn.c',
  'page-wifi.c',
  'page-wifi-security.c',
  'page-wireguard.c',
  'ppp-auth-methods-dialog.c',
  'vpn-helpers.c',
  'utils/utils.c',
  'shared/nm-utils/nm-compat.c',
  'shared/nm-utils/nm-shared-utils.c',
  'wireless-security/eap-method.c'
)

resource_data = files(
  'ce-ip4-routes.ui',
  'ce-ip6-routes.ui',
  'ce-new-connection.ui',
  'ce-page-bluetooth.ui',
  'ce-page-bond.ui',
  'ce-page-bridge-port.ui',
  'ce-page-bridge.ui',
  'ce-page-dcb.ui',
  'ce-page-dsl.ui',
  'ce-page-ethernet.ui',
  'ce-page-general.ui',
  'ce-page-infiniband.ui',
  'ce-page-ip4.ui',
  'ce-page-ip6.ui',
  'ce-page-ip-tunnel.ui',
  'ce-page-macsec.ui',
  'ce-page-mobile.ui',
  'ce-page-ppp.ui',
  'ce-page-proxy.ui',
  'ce-page-team-port.ui',
  'ce-page-team.ui',
  'ce-page-vlan.ui',
  'ce-page-wifi-security.ui',
  'ce-page-wifi.ui',
  'ce-page-wireguard.ui',
  'ce-ppp-auth-methods.ui',
  'gtk/menus.ui',
  'nm-connection-editor.ui',
  'nm-connection-list.ui'
)

gnome = import ('gnome')
sources += gnome.compile_resources(
  'ce-resources',
  'ce.gresource.xml',
  dependencies: resource_data
)

gtk = dependency('gtk+-3.0')
netman = dependency('libnm')
nma = dependency('libnma')
selinux = dependency('libselinux')
jansson = dependency('jansson', version: '>= 2.7')
m_dep = meson.get_compiler('c').find_library('m')

deps = [ gtk, netman, nma, selinux, jansson, m_dep ]

executable(
  'lp-connection-editor',
  sources,
  include_directories: [ '..', './utils/', './shared/', './wireless-security/' ],
  dependencies: deps,
  c_args : [ '-DNMALOCALEDIR="@0@"'.format(locale_dir) ],
  install: true
)
