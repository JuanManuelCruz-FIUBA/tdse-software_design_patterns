################################################################################
# Automatically-generated file. Do not edit!
# Toolchain: GNU Tools for STM32 (13.3.rel1)
################################################################################

-include ../makefile.init

RM := rm -rf

# All of the sources participating in the build are defined here
-include sources.mk
-include app/src/subdir.mk
-include Drivers/STM32F1xx_HAL_Driver/Src/subdir.mk
-include Core/Startup/subdir.mk
-include Core/Src/subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(S_DEPS)),)
-include $(S_DEPS)
endif
ifneq ($(strip $(S_UPPER_DEPS)),)
-include $(S_UPPER_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
endif

-include ../makefile.defs

OPTIONAL_TOOL_DEPS := \
$(wildcard ../makefile.defs) \
$(wildcard ../makefile.init) \
$(wildcard ../makefile.targets) \


BUILD_ARTIFACT_NAME := tdse-tp0_03-cyclic_executive
BUILD_ARTIFACT_EXTENSION := elf
BUILD_ARTIFACT_PREFIX :=
BUILD_ARTIFACT := $(BUILD_ARTIFACT_PREFIX)$(BUILD_ARTIFACT_NAME)$(if $(BUILD_ARTIFACT_EXTENSION),.$(BUILD_ARTIFACT_EXTENSION),)

# Add inputs and outputs from these tool invocations to the build variables 
EXECUTABLES += \
tdse-tp0_03-cyclic_executive.elf \

MAP_FILES += \
tdse-tp0_03-cyclic_executive.map \

SIZE_OUTPUT += \
default.size.stdout \

OBJDUMP_LIST += \
tdse-tp0_03-cyclic_executive.list \


# All Target
all: main-build

# Main-build Target
main-build: tdse-tp0_03-cyclic_executive.elf secondary-outputs

# Tool invocations
tdse-tp0_03-cyclic_executive.elf tdse-tp0_03-cyclic_executive.map: $(OBJS) $(USER_OBJS) C:\JMCruz\ST\STM32CubeIDE_1.19.0\TdSE_workspace\tdse-tp0_03-cyclic_executive\STM32F103RBTX_FLASH.ld makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-gcc -o "tdse-tp0_03-cyclic_executive.elf" @"objects.list" $(USER_OBJS) $(LIBS) -mcpu=cortex-m3 -T"C:\JMCruz\ST\STM32CubeIDE_1.19.0\TdSE_workspace\tdse-tp0_03-cyclic_executive\STM32F103RBTX_FLASH.ld" --specs=nosys.specs -Wl,-Map="tdse-tp0_03-cyclic_executive.map" -Wl,--gc-sections -static -specs=rdimon.specs --specs=nano.specs -mfloat-abi=soft -mthumb -Wl,--start-group -lc -lm -Wl,--end-group
	@echo 'Finished building target: $@'
	@echo ' '

default.size.stdout: $(EXECUTABLES) makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-size  $(EXECUTABLES)
	@echo 'Finished building: $@'
	@echo ' '

tdse-tp0_03-cyclic_executive.list: $(EXECUTABLES) makefile objects.list $(OPTIONAL_TOOL_DEPS)
	arm-none-eabi-objdump -h -S $(EXECUTABLES) > "tdse-tp0_03-cyclic_executive.list"
	@echo 'Finished building: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) default.size.stdout tdse-tp0_03-cyclic_executive.elf tdse-tp0_03-cyclic_executive.list tdse-tp0_03-cyclic_executive.map
	-@echo ' '

secondary-outputs: $(SIZE_OUTPUT) $(OBJDUMP_LIST)

fail-specified-linker-script-missing:
	@echo 'Error: Cannot find the specified linker script. Check the linker settings in the build configuration.'
	@exit 2

warn-no-linker-script-specified:
	@echo 'Warning: No linker script specified. Check the linker settings in the build configuration.'

.PHONY: all clean dependents main-build fail-specified-linker-script-missing warn-no-linker-script-specified

-include ../makefile.targets
