# Stop Command

This document defines the "stop" command workflow. When a user requests to "run stop" or simply types "stop", execute the following commands sequentially to gracefully shut down the development environment.

## Overview

Stop the backend services first, then stop the web-app frontend server to ensure a clean shutdown.

## Command Usage

When a user says:

- "run stop"

Execute the stop sequence to gracefully shut down both frontend and backend services.

## Commands to Execute

Execute these commands **sequentially**:

1. **Stop Backend Services** (First)

   - Command: `./cc.stop`
   - Permissions Required: `network`
   - Run as: Background process
   - **Wait for:** Output containing "All containers stopped successfully."

2. **Stop All Web App Frontend Localhosts** (After the backend services successfully stopped)

   a. **Check for all Ember localhosts:**

   - Command: `lsof -i -P -n | grep LISTEN`
   - Permissions Required: `all`
   - Purpose: Identify if Ember server is running and get its PID
   - Find all localhost ports named "node" and "ruby"

   b. **Kill all the processes if running:**

   - Command: `kill -9 $(lsof -ti :"PORT NAMED 'NODE' OR 'RUBY'")`
   - Permissions Required: `all`
   - Only execute if lsof found a running process

   c. **Verify all the processes are stopped:**

   - Command: `lsof -i -P -n | grep LISTEN`
   - Expected: No output

3. **If all successfully stopped, inform the user**

## Execution Notes

- First, run the backend stop script to shut down all backend services
- The cc.stop script will handle stopping all backend services gracefully
- After backend services are stopped, check if the Ember server is running using lsof
- If a process is found (node or ruby), forcefully kill it using kill -9
- Verify that all frontend processes are stopped

## Expected Behavior

After running these commands:

- All backend services will be stopped
- Ember web app server will be stopped (all node and ruby processes freed)
- Development environment will be fully shut down

## Error Handling

**CRITICAL: Do not automatically retry or run other commands on failure.**

If any step fails:

1. Report the error to the user
2. Show the error output
3. STOP execution - do not proceed to the next step
4. Wait for the user to manually address the issue

The user must explicitly request to retry or run other commands.
