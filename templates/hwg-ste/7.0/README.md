# HWg-STE Zabbix Template

## Overview

This Zabbix template provides comprehensive monitoring for HWg-STE Ethernet thermometer devices. The template monitors both temperature and humidity sensors with configurable thresholds and alerting capabilities.

### Key Features
- **Temperature Monitoring**: Real-time temperature monitoring with multiple alert thresholds
- **Humidity Monitoring**: Relative humidity tracking with dry/humid condition alerts
- **SNMP Integration**: Uses SNMP agent for data collection
- **Graphical Visualization**: Built-in graphs for both temperature and humidity trends
- **Flexible Thresholds**: Multiple trigger levels for different alert severities

## Template Details

- **Template Name**: HWg-STE
- **Zabbix Version**: 7.4
- **Template Group**: Ethernet thermometer

## Macros Used

| Name | Description | Default | Type |
|------|-------------|---------|------|
| `{$SENSORID}` | Sensor identifier filter | `>=1` | Text macro |

## Items Collected

### Temperature Monitoring
- **Name**: Temperature [Sensor 215]
- **Type**: SNMP Agent
- **Key**: `.3.1.5.1`
- **SNMP OID**: `.1.3.6.1.4.1.21796.4.1.3.1.5.1`
- **Units**: °C
- **Preprocessing**: Multiplier (0.1)
- **Description**: Monitors temperature readings from the HWg-STE sensor

### Humidity Monitoring
- **Name**: Humidity [Sensor 216]
- **Type**: SNMP Agent
- **Key**: `.3.1.5.2`
- **SNMP OID**: `.1.3.6.1.4.1.21796.4.1.3.1.5.2`
- **Units**: %RH
- **Preprocessing**: Multiplier (0.1)
- **Description**: Monitors relative humidity readings from the HWg-STE sensor

## Triggers

### Temperature Triggers
| Name | Expression | Priority | Description |
|------|------------|----------|-------------|
| Critical temperature (> 33°C) | `last(/HWg-STE/.3.1.5.1)>30` | High | Alerts when temperature exceeds 30°C (actual 33°C after preprocessing) |
| Temperature exceeded (> 26°C) | `last(/HWg-STE/.3.1.5.1)>26` | Average | Alerts when temperature exceeds 26°C |
| Temperature reached (> 23°C) | `last(/HWg-STE/.3.1.5.1)>23` | Info | Informational alert when temperature exceeds 23°C |
| Temperature too low (<14°C) | `last(/HWg-STE/.3.1.5.1)<14` | Warning | Alerts when temperature drops below 14°C |

### Humidity Triggers
| Name | Expression | Priority | Description |
|------|------------|----------|-------------|
| a bit dry (Humidity < 35%RH) | `last(/HWg-STE/.3.1.5.2)<35` | Warning | Alerts when humidity drops below 35% |
| a bit humid (Humidity > 55%RH) | `last(/HWg-STE/.3.1.5.2)>55` | Warning | Alerts when humidity exceeds 55% |

## Graphs

### Temperature Graph
- **Name**: Temperature [Sensor 215]
- **Color**: Green (#199C0D)
- **Description**: Displays temperature trends over time

### Humidity Graph
- **Name**: Humidity [Sensor 216]
- **Color**: Green (#199C0D)
- **Description**: Displays humidity trends over time

## Installation and Usage

1. **Import Template**: Import the `hwg-ste-template.yaml` file into your Zabbix server
2. **Configure Host**: Link the HWg-STE template to your HWg-STE device host
3. **SNMP Configuration**: Ensure SNMP is properly configured on your HWg-STE device
4. **Verify Connectivity**: Check that the SNMP OIDs are accessible from your Zabbix server

## SNMP Requirements

The template uses the following SNMP OIDs:
- Temperature: `.1.3.6.1.4.1.21796.4.1.3.1.5.1`
- Humidity: `.1.3.6.1.4.1.21796.4.1.3.1.5.2`

Ensure your HWg-STE device supports these OIDs and SNMP is enabled.

## Template Links

There are no template links in this template.

## Discovery Rules

There are no discovery rules in this template.

## Notes

- The template includes preprocessing to multiply values by 0.1, which should be considered when interpreting trigger thresholds
- Temperature values are displayed in Celsius (°C)
- Humidity values are displayed as relative humidity (%RH)
- All graphs use a green color scheme for consistency
