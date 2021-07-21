#!/bin/bash
# Script: temperatura-pi.sh
# Purpose: Visualizzare la temperatura di ARM CPU e GPU su  Raspberry Pi 2/3
# -------------------------------------------------------
cpu=$(</sys/class/thermal/thermal_zone0/temp)
gpu=$(/opt/vc/bin/vcgencmd measure_temp)
echo "--------------------------------------------"
echo "$(date) @ $(hostname)"
echo "--------------------------------------------"

if (( ${gpu:5:2} \> 80)); then
echo "Temperatura GPU elevata! => ${gpu:5}";
elif (( ${gpu:5:2} \> 64)); then
echo "Temperatura GPU alta => ${gpu:5}";
else
echo "Temperatura GPU nei limiti => ${gpu:5}";
fi

case $((cpu/1000)) in
        90) echo "Allarme!!! Temperatura CPU oltre i limiti => $((cpu/1000))'C";;
        8[5-9]) echo "Temperatura CPU molto elevata! => $((cpu/1000))'C";;
        8[0-4]) echo "Temperatura CPU elevata! => $((cpu/1000))'C";;
        7?) echo "Temperatura CPU alta => $((cpu/1000))'C";;
        6?) echo "Temperatura CPU medio alta => $((cpu/1000))'C";;
        *) echo "Temperatura CPU nei limiti => $((cpu/1000))'C";;
esac
