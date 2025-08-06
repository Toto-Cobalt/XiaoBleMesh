cmake_minimum_required(VERSION 3.20.0)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})

macro(app_set_runner_args)
  board_runner_args(dfu-util "--dfuse-modifiers=force:mass-erase")
  board_runner_args(pyocd "--erase")
  board_runner_args(nrfjprog "--erase")
endmacro()

# This find_package command locates the Zephyr package and sets up
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(XiaoBleMesh)

# NORDIC SDK APP START
target_sources(app PRIVATE
	src/main.c
	src/lb_service_handler.c
	src/model_handler.c)
target_include_directories(app PRIVATE include)
