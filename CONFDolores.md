# Configurações Mecânicas 

# Temperatura 

 100k beta 3950 1% thermistor (4.7k pullup), [https://pt.aliexpress.com/item/3D-Printer-All-metal-J-head-Hotend](https://pt.aliexpress.com/item/3D-Printer-All-metal-J-head-Hotend-with-Cooling-Fan-PTFE-Tubing-for-1-75MM-E3D/32705472496.html?spm=a2g0s.9042311.0.0.DS76CU)
```
#define TEMP_SENSOR_0 11
#define TEMP_SENSOR_1 0
```

## Direção de movimento dos eixos
```
#define INVERT_X_DIR true    
#define INVERT_Y_DIR false     
#define INVERT_Z_DIR true   
```

## Velocidade 

Movimentação para origem. 
 
``` 
#define HOMING_FEEDRATE {40*60, 40*60, 4*60, 0}  // set the homing speeds (mm/min)

```
## Passos por milimetros

```
#define DEFAULT_AXIS_STEPS_PER_UNIT   {80,80,2560.0,6.3}
```
