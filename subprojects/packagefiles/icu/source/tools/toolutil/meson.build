sources = files(
  'collationinfo.cpp',
  'dbgutil.cpp',
  'denseranges.cpp',
  'filestrm.cpp',
  'filetools.cpp',
  'flagparser.cpp',
  'package.cpp',
  'pkg_genc.cpp',
  'pkg_gencmn.cpp',
  'pkg_icu.cpp',
  'pkgitems.cpp',
  'ppucd.cpp',
  'swapimpl.cpp',
  'toolutil.cpp',
  'ucbuf.cpp',
  'ucln_tu.cpp',
  'ucm.cpp',
  'ucmstate.cpp',
  'udbgutil.cpp',
  'unewdata.cpp',
  'uoptions.cpp',
  'uparse.cpp',
  'writesrc.cpp',
  'xmlparser.cpp',
)

toolutil_c_args = ['-DU_TOOLUTIL_IMPLEMENTATION']
toolutil_cpp_args = ['-DU_TOOLUTIL_IMPLEMENTATION']

if have_elf_h
  toolutil_c_args += ['-DU_HAVE_ELF_H']
  toolutil_cpp_args += ['-DU_HAVE_ELF_H']
endif

toolutil_lib = library(
  'toolutil',
  sources,
  c_args: toolutil_c_args,
  cpp_args: toolutil_cpp_args,
  dependencies: icui18n_dep,
)

if meson.can_run_host_binaries()
  toolutil_native_lib = toolutil_lib
else
  toolutil_native_lib = library(
    'toolutil-native',
    sources,
    c_args: toolutil_c_args,
    cpp_args: toolutil_cpp_args,
    dependencies: icui18n_native_dep,
    native: true,
  )
endif

toolinc = include_directories('.')

toolutil_dep = declare_dependency(
  link_with: toolutil_lib,
  dependencies: icui18n_dep,
  include_directories: toolinc,
)

toolutil_native_dep = declare_dependency(
  link_with: toolutil_native_lib,
  dependencies: icui18n_native_dep,
  include_directories: toolinc,
)
