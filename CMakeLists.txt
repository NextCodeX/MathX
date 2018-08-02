# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (MathX)

# 设置主/副版本号
set (MathX_VERSION_MAJOR 1)
set (MathX_VERSION_MINOR 0)

set (CMAKE_INCLUDE_CURRENT_DIR ON)

# 加入一个配置头文件，用于处理 CMake 对源码的设置
configure_file (
  "${PROJECT_SOURCE_DIR}/config.h.in"
  "${PROJECT_BINARY_DIR}/config.h"
  )
 
# 是否使用自己的 MathFunctions 库
option (USE_MYMATH
	   "Use provided math implementation" ON)

# 是否加入 MathFunctions 库
if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/math")
  add_subdirectory (math)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)

# 指定生成目标
add_executable(MathX ${DIR_SRCS})
target_link_libraries (MathX ${EXTRA_LIBS})

# 指定安装路径
install (TARGETS MathX DESTINATION bin)
install (FILES "${PROJECT_BINARY_DIR}/config.h"
         DESTINATION include)

# 启用测试
enable_testing()

# 测试程序是否成功运行
add_test (test_run MathX 5 2)

# 测试帮助信息是否可以正常提示
add_test (test_usage MathX)
set_tests_properties (test_usage
  PROPERTIES PASS_REGULAR_EXPRESSION "Usage: .* base exponent")

# 定义一个宏，用来简化测试工作
macro (do_test arg1 arg2 result)
  add_test (test_${arg1}_${arg2} MathX ${arg1} ${arg2})
  set_tests_properties (test_${arg1}_${arg2}
    PROPERTIES PASS_REGULAR_EXPRESSION ${result})
endmacro (do_test)

# 利用 do_test 宏，测试一系列数据
do_test (5 2 "is 25")
do_test (10 5 "is 100000")
do_test (2 10 "is 1024")

# 构建 CPack 安装包
include (InstallRequiredSystemLibraries)
set (CPACK_RESOURCE_FILE_LICENSE
  "${CMAKE_CURRENT_SOURCE_DIR}/LICENSE")
set (CPack_PACKAGE_VERSION_MAJOR "${MathX_VERSION_MAJOR}")
set (CPack_PACKAGE_VERSION_MINOR "${MathX_VERSION_MINOR}")
include (CPack)