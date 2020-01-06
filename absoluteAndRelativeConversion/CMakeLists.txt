cmake_minimum_required(VERSION 3.1.0)

project(test)

# 测试用的两个变量
set(relativePath "path/to/test")
set(relativeFile test/a/b/c/test.txt)
# 用get_filename_component函数转换成绝对路径
get_filename_component(absPath ${relativePath} ABSOLUTE BASE_DIR
                       ${CMAKE_CURRENT_LIST_DIR})
message(${absPath})
# 相对路径可以用string函数的replace将绝对路径转换成相对路径
string(REPLACE ${CMAKE_CURRENT_LIST_DIR} "" relativePathNew ${absPath})
message(${relativePathNew})
# 提取文件名 文件扩展 文件路径，直接用相对路径提取，得到相对路径
get_filename_component(fileName ${relativeFile} NAME) # 得到带扩展名的文件名
message(${fileName})
get_filename_component(fileName ${relativeFile} NAME_WLE) # 得到不带扩展名的文件名
message(${fileName})
get_filename_component(fileName ${relativeFile} LAST_EXT) # 得到最后的扩展名
message(${fileName})
get_filename_component(filePath ${relativeFile} DIRECTORY) # 得到前面的路径，路径为相对路径
message(${filePath})
