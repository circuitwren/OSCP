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
