# File Transfer

## Computer to LLM-GPU With Tailscale

```bash
scp <FILE> sam@llm-gpu:~/
scp -r <FOLDER> sam@llm-gpu:~/
```

## LLM-GPU to Computer With Tailscale

```bash
scp sam@llm-gpu:/path/to/file .
scp -r sam@llm-gpu:/path/to/folder .
```

## Computer to LLM-GPU Without Tailscale

```bash
scp <FILE> sam@10.44.0.170:~/
scp -r <FOLDER> sam@10.44.0.170:~/
```

## LLM-GPU to Computer Without Tailscale

```bash
scp sam@10.44.0.170:/path/to/file .
scp -r sam@10.44.0.170:/path/to/folder .
```

## Transfer Using SSH Alias

```bash
scp <FILE> llm-gpu:~/
scp -r <FOLDER> llm-gpu:~/
scp llm-gpu:/path/to/file .
scp -r llm-gpu:/path/to/folder .
```

## Transfer With Progress and Resume

### Computer to LLM-GPU

```bash
rsync -avhP <FILE_OR_FOLDER> sam@llm-gpu:/path/to/destination/
```

### LLM-GPU to Computer

```bash
rsync -avhP sam@llm-gpu:/path/to/file-or-folder/ .
```

## Transfer Using Public IP

```bash
scp -P 2222 <FILE> sam@<PUBLIC_IP>:~/
scp -P 2222 sam@<PUBLIC_IP>:/path/to/file .
```

```bash
rsync -avhP -e "ssh -p 2222" <FILE_OR_FOLDER> sam@<PUBLIC_IP>:/path/to/destination/
```

## Voice Memo to Transcription Folder

```bash
scp "<RECORDING>.m4a" sam@llm-gpu:~/private-transcription/audio/
```

## Download Transcription Results

```bash
scp -r sam@llm-gpu:~/private-transcription/output/ .
```

## Create Transfer Archive

```bash
tar -czf archive.tar.gz <FOLDER>
```

## Extract Transfer Archive

```bash
tar -xzf archive.tar.gz
```

## Check File

```bash
ls -lh <FILE>
sha256sum <FILE>
```