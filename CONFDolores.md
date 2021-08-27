# Configurações Mecânicas 

# Temperatura 

 100k beta 3950 1% thermistor (4.7k pullup), [https://pt.aliexpress.com/item/3D-Printer-All-metal-J-head-Hotend](https://pt.aliexpress.com/item/3D-Printer-All-metal-J-head-Hotend-with-Cooling-Fan-PTFE-Tubing-for-1-75MM-E3D/32705472496.html?spm=a2g0s.9042311.0.0.DS76CU)
```
#define TEMP_SENSOR_0 11
#define TEMP_SENSOR_1 0
```

## Direção de movimento dos eixos
```
 INVERT_X_DIR true    
 INVERT_Y_DIR false     
 INVERT_Z_DIR true   
```

## Homing 
```
X_MIN_ENDSTOP_INVERTING true 
Y_MIN_ENDSTOP_INVERTING true
Z_MIN_ENDSTOP_INVERTING true 
```

## Motion 

Movimentação para origem. 
 
``` 
DEFAULT_AXIS_STEPS_PER_UNIT { 80, 80, 2560, 100}
DEFAULT_MAX_FEEDRATE { 300, 300, 2.5, 25 }
DEFAULT_MAX_ACCELERATION { 300, 300, 100, 100 }
DEFAULT_ACCELERATION 200 
DEFAULT_RETRACT_ACCELERATION 200 
DEFAULT_TRAVEL_ACCELERATION 200 


```

