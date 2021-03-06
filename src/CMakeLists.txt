#   Copyright 2018 Comcast Cable Communications Management, LLC
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.

cmake_minimum_required(VERSION 2.8.7)

set(PROJ_REBAR rebar-c)


file(GLOB HEADERS rebar-c.h cvs-hashmap.h symbol-table-map.h)
set(SOURCES linked_list.c cvs-hashmap.c symbol-table-map.c)


add_library(${PROJ_REBAR} STATIC ${HEADERS} ${SOURCES})
add_library(${PROJ_REBAR}.shared SHARED ${HEADERS} ${SOURCES})
set_target_properties(${PROJ_REBAR}.shared PROPERTIES OUTPUT_NAME ${PROJ_REBAR})

install (TARGETS ${PROJ_REBAR} DESTINATION lib${LIB_SUFFIX})
install (TARGETS ${PROJ_REBAR}.shared DESTINATION lib${LIB_SUFFIX})
install (FILES rebar-c.h cvs-hashmap.h DESTINATION include/${PROJ_REBAR})
