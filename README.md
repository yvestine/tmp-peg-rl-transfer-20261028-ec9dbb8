# 单孔 peg RL 临时传输

仅用于将单孔 RL 权重和接入资料传至另一台机器，下载并核对完成后删除本仓库。

## 下载后使用

```bash
sha256sum -c SHA256SUMS
unzip peg_single_hole_rl_bundle_20261028.zip
cd peg_single_hole_rl_bundle_20261028
sha256sum -c SHA256SUMS
python verify_actor.py
```

`verify_actor.py` 需要有 PyTorch 和 NumPy 的 Python 环境，只做 CPU 加载及输出检查。真机部署说明见包内 `DEPLOYMENT_CN.md`；包内含 residual PPO checkpoint、Actor 和门控源代码，不含 TAVLA 大模型权重或已经完成验收的真机执行桥。

配套单孔 Encoder TAVLA 在服务器运行；当前 RL 代码由控制客户端加载。保持每个 VLA action_chunk 执行 10 步，RL 按 10 Hz 更新。

## 删除临时传输

下载完成后，从 GitHub 仓库 Settings → General → Danger Zone → Delete this repository 删除整个临时仓库。单独删除 ZIP 文件仍会保留 Git 历史中的内容。删除远端仓库不会删除已经 clone 到本地的文件。
