#
#

add_library(adf STATIC
	adf_bitm.c
        adf_disk.c
        adf_file.c
        adf_raw.c
        adf_cache.c
        adf_dump.c
        adf_hd.c
        adf_salv.c
        adf_dir.c
        adf_env.c
        adf_link.c
        adf_util.c
	${NATIV_DIR}/adf_nativ.c
)

target_include_directories(adf PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}/${NATIV_DIR}"
	"${CMAKE_CURRENT_SOURCE_DIR}"
	
)
