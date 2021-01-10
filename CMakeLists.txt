cmake_minimum_required(VERSION 3.13)
project(dpdk-17.05.1 C)

set(CMAKE_CXX_STANDARD 11)

#[[if(CMAKE_COMPILER_IS_GNUCXX)
    #    add_compile_options(-std=c++11)
    set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")
    message(STATUS "optional:-std=c++11")
endif(CMAKE_COMPILER_IS_GNUCXX)]]

#[[set(RTE_SDK F:\\workspace\\c\\dpdk)]]
#[[set(RTE_TARGET x86_64-native-linuxapp-gcc)]]
set(DPDK_LIB F:\\workspace\\sword-graduate\\dpdk-17.05.1\\lib)
#[[set(DPDK_LIB ${RTE_SDK}\\lib)]]

set(SOURCE_FILE
        examples/l2fwd/main.c)

set(WERROR_FLAGS
        -W
        -Wall
        #        -Wstrict-prototypes
        #        -Wmissing-prototypes
        -Wmissing-declarations
        #        -Wold-style-definition
        -Wpointer-arith
        -Wcast-align
        #        -Wnested-externs
        -Wcast-qual
        -Wformat-nonliteral
        -Wformat-security
        -Wundef
        -Wwrite-strings
        -Wdeprecated)

#[[set(CFLAGS
        -m64
        -pthread
        -march=native
        -include ${RTE_SDK}/${RTE_TARGET}/include/rte_config.h
        -O3
        ${WERROR_FLAGS})]]

#[[set(DPDKLIBS
        -Wl,--whole-archive
        #        dpdk
        ${DPDK_LIB}\\librte_acl
        ${DPDK_LIB}\\librte_bbdev
        ${DPDK_LIB}\\librte_bitratestats
        ${DPDK_LIB}\\librte_bpf
        ${DPDK_LIB}\\librte_bus_dpaa
        ${DPDK_LIB}\\librte_bus_fslmc
        ${DPDK_LIB}\\librte_bus_ifpga
        ${DPDK_LIB}\\librte_bus_pci
        ${DPDK_LIB}\\librte_bus_vdev
        ${DPDK_LIB}\\librte_bus_vmbus
        ${DPDK_LIB}\\librte_cfgfile
        ${DPDK_LIB}\\librte_cmdline
        ${DPDK_LIB}\\librte_common_cpt
        ${DPDK_LIB}\\librte_common_dpaax
        ${DPDK_LIB}\\librte_common_octeontx
        ${DPDK_LIB}\\librte_compressdev
        ${DPDK_LIB}\\librte_cryptodev
        ${DPDK_LIB}\\librte_distributor
        ${DPDK_LIB}\\librte_eal
        ${DPDK_LIB}\\librte_efd
        ${DPDK_LIB}\\librte_ethdev
        ${DPDK_LIB}\\librte_eventdev
        ${DPDK_LIB}\\librte_flow_classify
        ${DPDK_LIB}\\librte_gro
        ${DPDK_LIB}\\librte_gso
        ${DPDK_LIB}\\librte_hash
        ${DPDK_LIB}\\librte_ip_frag
        ${DPDK_LIB}\\librte_jobstats
        ${DPDK_LIB}\\librte_kni
        ${DPDK_LIB}\\librte_kvargs
        ${DPDK_LIB}\\librte_latencystats
        ${DPDK_LIB}\\librte_lpm
        ${DPDK_LIB}\\librte_mbuf
        ${DPDK_LIB}\\librte_member
        ${DPDK_LIB}\\librte_mempool
        ${DPDK_LIB}\\librte_mempool_bucket
        ${DPDK_LIB}\\librte_mempool_dpaa2
        ${DPDK_LIB}\\librte_mempool_dpaa
        ${DPDK_LIB}\\librte_mempool_octeontx
        ${DPDK_LIB}\\librte_mempool_ring
        ${DPDK_LIB}\\librte_mempool_stack
        ${DPDK_LIB}\\librte_meter
        ${DPDK_LIB}\\librte_metrics
        ${DPDK_LIB}\\librte_net
        ${DPDK_LIB}\\librte_pci
        ${DPDK_LIB}\\librte_pdump
        ${DPDK_LIB}\\librte_pipeline
        ${DPDK_LIB}\\librte_pmd_af_packet
        ${DPDK_LIB}\\librte_pmd_ark
        ${DPDK_LIB}\\librte_pmd_atlantic
        ${DPDK_LIB}\\librte_pmd_avf
        ${DPDK_LIB}\\librte_pmd_avp
        ${DPDK_LIB}\\librte_pmd_axgbe
        ${DPDK_LIB}\\librte_pmd_bbdev_null
        ${DPDK_LIB}\\librte_pmd_bnxt
        ${DPDK_LIB}\\librte_pmd_bond
        ${DPDK_LIB}\\librte_pmd_caam_jr
        ${DPDK_LIB}\\librte_pmd_crypto_scheduler
        ${DPDK_LIB}\\librte_pmd_cxgbe
        ${DPDK_LIB}\\librte_pmd_dpaa2
        ${DPDK_LIB}\\librte_pmd_dpaa2_cmdif
        ${DPDK_LIB}\\librte_pmd_dpaa2_event
        ${DPDK_LIB}\\librte_pmd_dpaa2_qdma
        ${DPDK_LIB}\\librte_pmd_dpaa2_sec
        ${DPDK_LIB}\\librte_pmd_dpaa
        ${DPDK_LIB}\\librte_pmd_dpaa_event
        ${DPDK_LIB}\\librte_pmd_dpaa_sec
        ${DPDK_LIB}\\librte_pmd_dsw_event
        ${DPDK_LIB}\\librte_pmd_e1000
        ${DPDK_LIB}\\librte_pmd_ena
        ${DPDK_LIB}\\librte_pmd_enetc
        ${DPDK_LIB}\\librte_pmd_enic
        ${DPDK_LIB}\\librte_pmd_failsafe
        ${DPDK_LIB}\\librte_pmd_fm10k
        ${DPDK_LIB}\\librte_pmd_i40e
        ${DPDK_LIB}\\librte_pmd_ifc
        ${DPDK_LIB}\\librte_pmd_ifpga_rawdev
        ${DPDK_LIB}\\librte_pmd_ixgbe
        ${DPDK_LIB}\\librte_pmd_kni
        ${DPDK_LIB}\\librte_pmd_lio
        ${DPDK_LIB}\\librte_pmd_netvsc
        ${DPDK_LIB}\\librte_pmd_nfp
        ${DPDK_LIB}\\librte_pmd_null
        ${DPDK_LIB}\\librte_pmd_null_crypto
        ${DPDK_LIB}\\librte_pmd_octeontx
        ${DPDK_LIB}\\librte_pmd_octeontx_crypto
        ${DPDK_LIB}\\librte_pmd_octeontx_ssovf
        ${DPDK_LIB}\\librte_pmd_octeontx_zip
        ${DPDK_LIB}\\librte_pmd_opdl_event
        ${DPDK_LIB}\\librte_pmd_pcap
        ${DPDK_LIB}\\librte_pmd_qat
        ${DPDK_LIB}\\librte_pmd_qede
        ${DPDK_LIB}\\librte_pmd_ring
        ${DPDK_LIB}\\librte_pmd_sfc_efx
        ${DPDK_LIB}\\librte_pmd_skeleton_event
        ${DPDK_LIB}\\librte_pmd_skeleton_rawdev
        ${DPDK_LIB}\\librte_pmd_softnic
        ${DPDK_LIB}\\librte_pmd_sw_event
        ${DPDK_LIB}\\librte_pmd_tap
        ${DPDK_LIB}\\librte_pmd_thunderx_nicvf
        ${DPDK_LIB}\\librte_pmd_vdev_netvsc
        ${DPDK_LIB}\\librte_pmd_vhost
        ${DPDK_LIB}\\librte_pmd_virtio
        ${DPDK_LIB}\\librte_pmd_virtio_crypto
        ${DPDK_LIB}\\librte_pmd_vmxnet3_uio
        ${DPDK_LIB}\\librte_port
        ${DPDK_LIB}\\librte_power
        ${DPDK_LIB}\\librte_rawdev
        ${DPDK_LIB}\\librte_reorder
        ${DPDK_LIB}\\librte_ring
        ${DPDK_LIB}\\librte_sched
        ${DPDK_LIB}\\librte_security
        ${DPDK_LIB}\\librte_table
        ${DPDK_LIB}\\librte_timer
        ${DPDK_LIB}\\librte_vhost
        -Wl,--no-whole-archive)]]

add_definitions(
        -DRTE_MACHINE_CPUFLAG_SSE
        -DRTE_MACHINE_CPUFLAG_SSE2
        -DRTE_MACHINE_CPUFLAG_SSE3
        -DRTE_MACHINE_CPUFLAG_SSSE3
        -DRTE_MACHINE_CPUFLAG_SSE4_1
        -DRTE_MACHINE_CPUFLAG_SSE4_2
        -DRTE_MACHINE_CPUFLAG_AES
        -DRTE_MACHINE_CPUFLAG_PCLMULQDQ
        -DRTE_MACHINE_CPUFLAG_AVX
        -DRTE_MACHINE_CPUFLAG_RDRAND
        -DRTE_MACHINE_CPUFLAG_FSGSBASE
        -DRTE_MACHINE_CPUFLAG_F16C
        -DRTE_MACHINE_CPUFLAG_AVX2
        -D_GNU_SOURCE)

#[[add_compile_options(${CFLAGS})]]

#[[include_directories(${RTE_SDK}/${RTE_TARGET}/include)]]

include_directories(${DPDK_LIB}\\librte_acl)
include_directories(${DPDK_LIB}\\librte_bbdev)
include_directories(${DPDK_LIB}\\librte_bitratestats)
include_directories(${DPDK_LIB}\\librte_bpf)
include_directories(${DPDK_LIB}\\librte_bus_dpaa)
include_directories(${DPDK_LIB}\\librte_bus_fslmc)
include_directories(${DPDK_LIB}\\librte_bus_ifpga)
include_directories(${DPDK_LIB}\\librte_bus_pci)
include_directories(${DPDK_LIB}\\librte_bus_vdev)
include_directories(${DPDK_LIB}\\librte_bus_vmbus)
include_directories(${DPDK_LIB}\\librte_cfgfile)
include_directories(${DPDK_LIB}\\librte_cmdline)
include_directories(${DPDK_LIB}\\librte_common_cpt)
include_directories(${DPDK_LIB}\\librte_common_dpaax)
include_directories(${DPDK_LIB}\\librte_common_octeontx)
include_directories(${DPDK_LIB}\\librte_compressdev)
include_directories(${DPDK_LIB}\\librte_cryptodev)
include_directories(${DPDK_LIB}\\librte_distributor)
include_directories(${DPDK_LIB}\\librte_eal\\include)
include_directories(${DPDK_LIB}\\librte_eal\\common\\include)
#include_directories(${DPDK_LIB}\\librte_eal\\common\\include\\arch\\x86)
include_directories(${DPDK_LIB}\\librte_efd)
include_directories(${DPDK_LIB}\\librte_ethdev)
include_directories(${DPDK_LIB}\\librte_eventdev)
include_directories(${DPDK_LIB}\\librte_flow_classify)
include_directories(${DPDK_LIB}\\librte_gro)
include_directories(${DPDK_LIB}\\librte_gso)
include_directories(${DPDK_LIB}\\librte_hash)
include_directories(${DPDK_LIB}\\librte_ip_frag)
include_directories(${DPDK_LIB}\\librte_jobstats)
include_directories(${DPDK_LIB}\\librte_kni)
include_directories(${DPDK_LIB}\\librte_kvargs)
include_directories(${DPDK_LIB}\\librte_latencystats)
include_directories(${DPDK_LIB}\\librte_lpm)
include_directories(${DPDK_LIB}\\librte_mbuf)
include_directories(${DPDK_LIB}\\librte_member)
include_directories(${DPDK_LIB}\\librte_mempool)
include_directories(${DPDK_LIB}\\librte_mempool_bucket)
include_directories(${DPDK_LIB}\\librte_mempool_dpaa2)
include_directories(${DPDK_LIB}\\librte_mempool_dpaa)
include_directories(${DPDK_LIB}\\librte_mempool_octeontx)
include_directories(${DPDK_LIB}\\librte_mempool_ring)
include_directories(${DPDK_LIB}\\librte_mempool_stack)
include_directories(${DPDK_LIB}\\librte_meter)
include_directories(${DPDK_LIB}\\librte_metrics)
include_directories(${DPDK_LIB}\\librte_net)
include_directories(${DPDK_LIB}\\librte_pci)
include_directories(${DPDK_LIB}\\librte_pdump)
include_directories(${DPDK_LIB}\\librte_pipeline)
include_directories(${DPDK_LIB}\\librte_pmd_af_packet)
include_directories(${DPDK_LIB}\\librte_pmd_ark)
include_directories(${DPDK_LIB}\\librte_pmd_atlantic)
include_directories(${DPDK_LIB}\\librte_pmd_avf)
include_directories(${DPDK_LIB}\\librte_pmd_avp)
include_directories(${DPDK_LIB}\\librte_pmd_axgbe)
include_directories(${DPDK_LIB}\\librte_pmd_bbdev_null)
include_directories(${DPDK_LIB}\\librte_pmd_bnxt)
include_directories(${DPDK_LIB}\\librte_pmd_bond)
include_directories(${DPDK_LIB}\\librte_pmd_caam_jr)
include_directories(${DPDK_LIB}\\librte_pmd_crypto_scheduler)
include_directories(${DPDK_LIB}\\librte_pmd_cxgbe)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa2)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa2_cmdif)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa2_event)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa2_qdma)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa2_sec)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa_event)
include_directories(${DPDK_LIB}\\librte_pmd_dpaa_sec)
include_directories(${DPDK_LIB}\\librte_pmd_dsw_event)
include_directories(${DPDK_LIB}\\librte_pmd_e1000)
include_directories(${DPDK_LIB}\\librte_pmd_ena)
include_directories(${DPDK_LIB}\\librte_pmd_enetc)
include_directories(${DPDK_LIB}\\librte_pmd_enic)
include_directories(${DPDK_LIB}\\librte_pmd_failsafe)
include_directories(${DPDK_LIB}\\librte_pmd_fm10k)
include_directories(${DPDK_LIB}\\librte_pmd_i40e)
include_directories(${DPDK_LIB}\\librte_pmd_ifc)
include_directories(${DPDK_LIB}\\librte_pmd_ifpga_rawdev)
include_directories(${DPDK_LIB}\\librte_pmd_ixgbe)
include_directories(${DPDK_LIB}\\librte_pmd_kni)
include_directories(${DPDK_LIB}\\librte_pmd_lio)
include_directories(${DPDK_LIB}\\librte_pmd_netvsc)
include_directories(${DPDK_LIB}\\librte_pmd_nfp)
include_directories(${DPDK_LIB}\\librte_pmd_null)
include_directories(${DPDK_LIB}\\librte_pmd_null_crypto)
include_directories(${DPDK_LIB}\\librte_pmd_octeontx)
include_directories(${DPDK_LIB}\\librte_pmd_octeontx_crypto)
include_directories(${DPDK_LIB}\\librte_pmd_octeontx_ssovf)
include_directories(${DPDK_LIB}\\librte_pmd_octeontx_zip)
include_directories(${DPDK_LIB}\\librte_pmd_opdl_event)
include_directories(${DPDK_LIB}\\librte_pmd_pcap)
include_directories(${DPDK_LIB}\\librte_pmd_qat)
include_directories(${DPDK_LIB}\\librte_pmd_qede)
include_directories(${DPDK_LIB}\\librte_pmd_ring)
include_directories(${DPDK_LIB}\\librte_pmd_sfc_efx)
include_directories(${DPDK_LIB}\\librte_pmd_skeleton_event)
include_directories(${DPDK_LIB}\\librte_pmd_skeleton_rawdev)
include_directories(${DPDK_LIB}\\librte_pmd_softnic)
include_directories(${DPDK_LIB}\\librte_pmd_sw_event)
include_directories(${DPDK_LIB}\\librte_pmd_tap)
include_directories(${DPDK_LIB}\\librte_pmd_thunderx_nicvf)
include_directories(${DPDK_LIB}\\librte_pmd_vdev_netvsc)
include_directories(${DPDK_LIB}\\librte_pmd_vhost)
include_directories(${DPDK_LIB}\\librte_pmd_virtio)
include_directories(${DPDK_LIB}\\librte_pmd_virtio_crypto)
include_directories(${DPDK_LIB}\\librte_pmd_vmxnet3_uio)
include_directories(${DPDK_LIB}\\librte_port)
include_directories(${DPDK_LIB}\\librte_power)
include_directories(${DPDK_LIB}\\librte_rawdev)
include_directories(${DPDK_LIB}\\librte_reorder)
include_directories(${DPDK_LIB}\\librte_ring)
include_directories(${DPDK_LIB}\\librte_sched)
include_directories(${DPDK_LIB}\\librte_security)
include_directories(${DPDK_LIB}\\librte_table)
include_directories(${DPDK_LIB}\\librte_timer)
include_directories(${DPDK_LIB}\\librte_vhost)

#[[include_directories(${DPDKLIBS})]]

#[[link_directories(${RTE_SDK}/${RTE_TARGET}/lib)]]

link_libraries(
        ${DPDKLIBS}
        #[[pthread
        rt
        dl
        m
        numa
        pcap]])

add_executable(dpdk-17.05.1
        ${SOURCE_FILE})