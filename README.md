## 必須ではない。localでdebugしたい場合
# gh extension install github/gh-aw
# gh aw init

# git 設定
git config --global user.email ""
git config --global user.name "testuser2"

## workflow for GitHub Actions self-hosted runner
.github/workflows/gh-aw-runner.yml

git add .github/workflows/gh-aw-runner.yml
# git add .github/aw/   # Agentic 指示がある場合
git commit -m "Add gh-aw runner workflow (PoC)"
git push origin test_mng_aw
## 必須ではない。localでdebugしたい場合
# gh extension install github/gh-aw
# gh aw init

# git 設定
git config --global user.email ""
coco2@DESKTOP-NI2MVC5:~/work/test_mng_aw$ git config --global user.name "testuser2"

## workflow for GitHub Actions self-hosted runner
.github/workflows/gh-aw-runner.yml

git add .github/workflows/gh-aw-runner.yml
# git add .github/aw/   # Agentic 指示がある場合
git commit -m "Add gh-aw runner workflow (PoC)"
git push origin test_mng_aw
