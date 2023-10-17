# Atualizações da Impressora 3D Florinda 

## Instalação do Marlin 
Baixar o firmware estável LTS (2.0.9.7) na [página oficial do Marlin](https://marlinfw.org/meta/download/) e fazer os ajustes nos arquivos de configuração. 

### Paramteros Ajustados 

```
// Choose the name from boards.h that matches your setup
#ifndef MOTHERBOARD
#define MOTHERBOARD BOARD_MKS_TINYBEE
#endif

#define BAUDRATE 115200

#define SERIAL_PORT_2 -1
#define BAUDRATE_2 115200 

//
// RepRapDiscount FULL GRAPHIC Smart Controller
// https://reprap.org/wiki/RepRapDiscount_Full_Graphic_Smart_Controller
//
#define REPRAP_DISCOUNT_FULL_GRAPHIC_SMART_CONTROLLER

/**
 * SD CARD
 *
 * SD Card support is disabled by default. If your controller has an SD slot,
 * you must uncomment the following option or it won't work.
 */
#define SDSUPPORT

/**
 * EEPROM
 *
 * Persistent storage to preserve configurable settings across reboots.
 *
 *   M500 - Store settings to EEPROM.
 *   M501 - Read settings from EEPROM. (i.e., Throw away unsaved changes)
 *   M502 - Revert settings to "factory" defaults. (Follow with M500 to init the EEPROM.)
 */
#define EEPROM_SETTINGS // Persistent storage with M500 and M501
// #define DISABLE_M503        // Saves ~2700 bytes of flash. Disable for release!
#define EEPROM_CHITCHAT    // Give feedback on EEPROM commands. Disable to save PROGMEM.
#define EEPROM_BOOT_SILENT // Keep M503 quiet and only give errors during first load
#if ENABLED(EEPROM_SETTINGS)
// #define EEPROM_AUTO_INIT  // Init EEPROM automatically on any errors.
// #define EEPROM_INIT_NOW   // Init EEPROM on first boot after a new build.
#endif

#define TEMP_SENSOR_BED 0

// This defines the number of extruders
// :[0, 1, 2, 3, 4, 5, 6, 7, 8]
#define EXTRUDERS 1

#define TEMP_SENSOR_0 1

#define TEMP_SENSOR_BED 0

// Mechanical endstop with COM to ground and NC to Signal uses "false" here (most common setup).
#define X_MIN_ENDSTOP_INVERTING true       // Set to true to invert the logic of the endstop.
#define Y_MIN_ENDSTOP_INVERTING true       // Set to true to invert the logic of the endstop.
#define Z_MIN_ENDSTOP_INVERTING true       // Set to true to invert the logic of the endstop.

#define DEFAULT_AXIS_STEPS_PER_UNIT \
  {                                 \
    80, 80, 2560, 100                \
  }

/**
 * Default Max Feed Rate (mm/s)
 * Override with M203
 *                                      X, Y, Z [, I [, J [, K]]], E0 [, E1[, E2...]]
 */
#define DEFAULT_MAX_FEEDRATE \
  {                          \
    300, 300, 2.5, 25          \
  }
  
  
/**
 * Default Acceleration (change/s) change = mm/s
 * Override with M204
 *
 *   M204 P    Acceleration
 *   M204 R    Retract Acceleration
 *   M204 T    Travel Acceleration
 */
#define DEFAULT_ACCELERATION 300         // X, Y, Z ... and E acceleration for printing moves
#define DEFAULT_RETRACT_ACCELERATION 300 // E acceleration for retracts
#define DEFAULT_TRAVEL_ACCELERATION 300  // X, Y, Z ... acceleration for travel (non printing) moves


// Invert the stepper direction. Change (or reverse the motor connector) if an axis goes the wrong way.
#define INVERT_X_DIR true
#define INVERT_Y_DIR true
#define INVERT_Z_DIR false


// Direction of endstops when homing; 1=MAX, -1=MIN
// :[-1,1]
#define X_HOME_DIR -1
#define Y_HOME_DIR -1
#define Z_HOME_DIR -1


// The size of the printable area
#define X_BED_SIZE 200
#define Y_BED_SIZE 200

/**
 * Continue after Power-Loss (Creality3D)
 *
 * Store the current state to the SD Card at the start of each layer
 * during SD printing. If the recovery file is found at boot time, present
 * an option on the LCD screen to continue the print from the last-known
 * point in the file.
 */
#define POWER_LOSS_RECOVERY
#if ENABLED(POWER_LOSS_RECOVERY)
#define PLR_ENABLED_DEFAULT true // Power Loss Recovery enabled by default. (Set with 'M413 Sn' & M500)

/**
 * Nozzle Park
 *
 * Park the nozzle at the given XYZ position on idle or G27.
 *
 * The "P" parameter controls the action applied to the Z axis:
 *
 *    P0  (Default) If Z is below park Z raise the nozzle.
 *    P1  Raise the nozzle always to Z-park height.
 *    P2  Raise the nozzle by Z-park amount, limited to Z_MAX_POS.
 */
#define NOZZLE_PARK_FEATURE

#if ENABLED(NOZZLE_PARK_FEATURE)
// Specify a park position as { X, Y, Z_raise }
#define NOZZLE_PARK_POINT                  \
  {                                        \
    (X_MIN_POS + 10), (Y_MAX_POS - 10), 20 \
  }
#define NOZZLE_PARK_MOVE 0          // Park motion: 0 = XY Move, 1 = X Only, 2 = Y Only, 3 = X before Y, 4 = Y before X
#define NOZZLE_PARK_Z_RAISE_MIN 2   // (mm) Always raise Z by at least this distance
#define NOZZLE_PARK_XY_FEEDRATE 100 // (mm/s) X and Y axes feedrate (also used for delta Z axis)
#define NOZZLE_PARK_Z_FEEDRATE 5    // (mm/s) Z axis feedrate (not used for delta printers)
#endif

/**
 * Advanced Pause for Filament Change
 *  - Adds the G-code M600 Filament Change to initiate a filament change.
 *  - This feature is required for the default FILAMENT_RUNOUT_SCRIPT.
 *
 * Requirements:
 *  - For Filament Change parking enable and configure NOZZLE_PARK_FEATURE.
 *  - For user interaction enable an LCD display, HOST_PROMPT_SUPPORT, or EMERGENCY_PARSER.
 *
 * Enable PARK_HEAD_ON_PAUSE to add the G-code M125 Pause and Park.
 */
#define ADVANCED_PAUSE_FEATURE

#define PARK_HEAD_ON_PAUSE // Park the nozzle during pause and filament change. 


/**
 * WiFi Support (Espressif ESP32 WiFi)
 */
// #define WIFISUPPORT         // Marlin embedded WiFi managenent
#define ESP3D_WIFISUPPORT // ESP3D Library WiFi management (https://github.com/luc-github/ESP3DLib)

```
## Instalação do Display 12864 
Ocorreu um ploblema na primeira ao instalar o Display genérico 12864 originalmente usado para RAMPS. Os conectores estão desalinhados e precisamos inverter a conexão, [ver este vídeo.](https://www.youtube.com/watch?v=vXFx7YDWYYI) 


## Referências 

* [Download Marlin](https://marlinfw.org/meta/download/)
* [Solved the problem: MKS motherboards are not compatable with non-MKS LCD2004/12864](https://www.youtube.com/watch?v=vXFx7YDWYYI) 
* [MKS TinyBee firmware configuration and connection router tutorial](https://www.youtube.com/watch?v=6KCa3XEugMY)
* [How To Install PlatformIO (ESP32 + Arduino series)](https://www.youtube.com/watch?v=5edPOlQQKmo) 
