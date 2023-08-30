Resources:
- [Stackoverflow](https://stackoverflow.com/questions/69244218/how-to-run-a-jupyter-notebook-through-a-remote-server-on-local-machine)

**Remote machine**
1. `jupyter notebook --no-browser --port=50000`
	- Or create an alias for this command above 
2. Copy the ip address: `xxx.xx.xxx.xxx`
3. Copy the token: statement followed by a `token=` - `{string}`

**Local machine**
4. Run: `ssh -L 50000:localhost:50000 <REMOTE_USER>@<REMOTE_HOST>`
4. Copy the ip address into your local web browser
5. An interface your prompt your for your token. Paste that in
