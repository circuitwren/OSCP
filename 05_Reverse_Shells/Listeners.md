Setting up multi-handlers, standard nc configs, and catching stable SSL shells.
# 🎧 Listeners & Shell Catching

### 🚀 FAST COPY (Click button on the right to copy instantly)
```bash
rlwrap nc -lvnp 4444
```

---

## Detailed Notes
Use the command above to start a Netcat listener on port 4444. 
The `rlwrap` part is important because it lets you use your arrow keys inside the hacked machine.

| Flag | Description |
| :--- | :---------- |
| -l | Listen mode, to wait for a connection to connect to us. |
| -v | Verbose mode, so that we know when we receive a connection. |
| -n | Disable DNS resolution and only connect from/to IPs, to speed up the connection. |
| -p 4444 | Port number netcat is listening on, and the reverse connection should be send to. |

