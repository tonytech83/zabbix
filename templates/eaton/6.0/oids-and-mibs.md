Eaton UPS SNMP OIDs and MIBs
Posted byVyacheslav03.01.2021 Leave a commenton Eaton UPS SNMP OIDs and MIBs
Once we installed an Eaton 9PX8KiPM rev01 + 9PXEBM240 rev02 UPS with a network card (Network MS) in one company, so I decided to write my template in Zabbix and, accordingly, I will post the SNMP OIDs that I used here.

You can check SNMP OID from Linux with the following command (where IXNFO.COM is SNMP community):

1
snmpwalk -v1 -c IXNFO.COM 192.168.5.5
I indicated the IP address on the network card by connecting to it with an ordinary console cable with an RJ45 connector (as for D-Link and Huawei switches, for example), in the same place you can reset the password if you suddenly forget. Then I typed the IP address of the UPS in the browser to open the web interface and specify the password for login and SNMP community.

Battery Information:

upsBatteryVoltage (V DC)
1.3.6.1.2.1.33.1.2.5
1.3.6.1.4.1.534.1.2.2.0

upsBatCapacity (%)
1.3.6.1.4.1.534.1.2.4.0

upsSecondsOnBattery
1.3.6.1.2.1.33.1.2.2
1.3.6.1.2.1.33.1.2.2.0

upsEstimatedMinutesRemaining
1.3.6.1.2.1.33.1.2.3
1.3.6.1.2.1.33.1.2.3.0

upsEstimatedChargeRemaining
1.3.6.1.2.1.33.1.2.4

upsBatTimeRemaining (Battery Runtime Remaining (sec.))
1.3.6.1.4.1.534.1.2.1.0

upsBatteryStatus (unknown(1),Normal(2),Low(3),Depleted(4))
1.3.6.1.2.1.33.1.2.1

upsBatteryAbmStatus (Charging(1),Discharging(2),Floating(3),Resting(4),unknown(5),Disconnected(6),Under Test(7),Check Battery(8))
1.3.6.1.4.1.534.1.2.5.0

upsTestBatteryStatus (unknown (1),passed (2),failed (3),inProgress (4),notSupported (5),inhibited (6),scheduled (7))
1.3.6.1.4.1.534.1.8.2.0

Voltage information and other:

upsInputFrequency (result multiplied by 0.1)
1.3.6.1.2.1.33.1.3.3.1.2
1.3.6.1.2.1.33.1.3.3.1.2.1
1.3.6.1.4.1.534.1.3.1.0

upsOutputFrequency (result multiplied by 0.1)
1.3.6.1.4.1.534.1.4.2.0

upsInputVoltage (V AC)
1.3.6.1.2.1.33.1.3.3.1.3
1.3.6.1.2.1.33.1.3.3.1.3.1
1.3.6.1.4.1.534.1.3.4.1.2.1

outputVoltage (result multiplied by 0.1)
1.3.6.1.4.1.705.1.7.2.1.2.1

upsOutputLoad (%)
1.3.6.1.4.1.534.1.4.1.0

upsOutputWatts (Output Watts (W))
1.3.6.1.4.1.534.1.4.4.1.4.1

upsEnvAmbientTemp (Internal Temperature (C))
1.3.6.1.4.1.534.1.6.1.0

upsInputSource (other(1),none(2),primaryUtility(3),bypassFeed(4),secondaryUtility(5),generator(6),flywheel(7),fuelcell(8))
1.3.6.1.4.1.534.1.3.5.0

upsOutputSource (other(1),none(2),normal(3),bypass(4),battery(5),booster(6),reducer(7),parallelCapacity(8),parallelRedundant(9),highEfficiencyMode(10))
1.3.6.1.4.1.534.1.4.5.0

upsAlarms (count)
1.3.6.1.4.1.534.1.7.1.0

upsConfigHighVoltageTransferPoint (V AC)
1.3.6.1.2.1.33.1.9.10.0

upsConfigLowVoltageTransferPoint (V AC)
1.3.6.1.2.1.33.1.9.9.0

1.3.6.1.2.1.33.1.1.1.0 (upsIdentManufacturer)
1.3.6.1.2.1.33.1.1.2.0 (upsIdentModel)
1.3.6.1.2.1.33.1.1.3.0 (upsIdentUPSSoftwareVersion)
1.3.6.1.2.1.33.1.1.4.0 (upsIdentAgentSoftwareVersion)
1.3.6.1.2.1.33.1.1.5.0 (upsIdentName)
1.3.6.1.2.1.33.1.9.9.0 (upsConfigLowVoltageTransferPoint)
1.3.6.1.2.1.33.1.9.10.0 (upsConfigHighVoltageTransferPoint)
1.3.6.1.4.1.534.1.10.8 (upsConfigInstallDate) Date of Installation
1.3.6.1.4.1.534.1.2.6 (upsBatteryLastRep) Battery Last Replaced Date

Standard SNMP OIDs:

1.3.6.1.2.1.1.1.0 (sysDescr)
1.3.6.1.2.1.1.2.0 (sysObjectID)
1.3.6.1.2.1.1.3.0 (sysUpTime)
1.3.6.1.2.1.1.4.0 (sysContact)
1.3.6.1.2.1.1.5.0 (sysName)
1.3.6.1.2.1.1.6.0 (sysLocation)
1.3.6.1.2.1.2.1.0 (ifNumber)
1.3.6.1.2.1.2.2.1.2 (ifDescr)
1.3.6.1.2.1.2.2.1.6 (ifPhysAddress)
1.3.6.1.2.1.2.2.1.10 (ifInOctets)
1.3.6.1.2.1.2.2.1.16 (ifOutOctets)

You can also download SNMP MIB from the official website
https://powerquality.eaton.com/support/software-drivers/downloads/connectivity-firmware.asp