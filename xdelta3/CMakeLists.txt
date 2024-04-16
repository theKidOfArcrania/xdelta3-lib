add_library(xdelta
  xdelta3-blkcache.h
  xdelta3-decode.h
  xdelta3-djw.h
  xdelta3-fgk.h
  xdelta3-hash.h
  xdelta3-internal.h
  xdelta3-list.h
  xdelta3-lzma.h
  xdelta3-main.h
  xdelta3-merge.h
  xdelta3-second.h
  xdelta3-test.h
  xdelta3-cfgs.h
  xdelta3.h
  xdelta3.c
)

target_link_libraries(xdelta)

# TODO: AX_CHECK_ALIGNED_ACCESS_REQUIRED
# TODO: lzma

include(CheckTypeSize)
check_type_size(size_t SIZE)
add_definitions(-DSIZEOF_SIZE_T=${SIZE})
check_type_size("unsigned int" SIZE)
add_definitions(-DSIZEOF_UNSIGNED_INT=${SIZE})
check_type_size("unsigned long" SIZE)
add_definitions(-DSIZEOF_UNSIGNED_LONG=${SIZE})
check_type_size("unsigned long long" SIZE)
add_definitions(-DSIZEOF_UNSIGNED_LONG_LONG=${SIZE})

add_definitions(-DSECONDARY_DJW=1 -DSECONDARY_FGK=1 -DXD3_ENCODER=1)
