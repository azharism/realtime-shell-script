#!/bin/bash

# Function to kill zombie processes
kill_zombies() {
    # Get list of zombie processes
    zombies=$(ps aux | awk '$8=="Z" {print $2}')

    if [ -n "$zombies" ]; then
        echo "Killing zombie processes..."
        # Kill each zombie process
        for zombie_pid in $zombies; do
            kill -9 "$zombie_pid"
        done
    else
        echo "No zombie processes found."
    fi
}

# Kill zombie processes
kill_zombies

# Get current date and time
date_time=$(date +"%Y-%m-%d %H:%M:%S")

# Get system uptime
uptime_info=$(uptime)

# Get CPU usage
cpu_info=$(top -bn1 | grep "Cpu(s)" | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk '{print 100 - $1}')

# Get memory usage
memory_info=$(free -m | grep Mem | awk '{print $3}')

# Get swap usage
swap_info=$(free -m | grep Swap | awk '{print $3}')

# Get number of zombie processes
zombie_processes=$(ps aux | awk '$8=="Z" {print $2}' | wc -l)

# Print system statistics
echo "Date and Time: $date_time"
echo "Uptime: $uptime_info"
echo "CPU Usage: $cpu_info%"
echo "Memory Usage: $memory_info MiB"
echo "Swap Usage: $swap_info MiB"
echo "Number of Zombie Processes: $zombie_processes"
