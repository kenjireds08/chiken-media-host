# chiken-media-host

Instagram 投稿用の**画像受け渡し置き場**。Cloudflare Pages で配信する。

## なぜ必要か

Instagram の Content Publishing API は、画像を**公開URLから取りに行く**方式で、ローカルファイルの直接アップロードに対応していない。そのため、投稿の瞬間だけ画像が公開URLで見える状態を作る必要がある。

## 運用

- `images/` に JPEG を置いて push すると、`https://chiken-media-host.pages.dev/images/<file>.jpg` で配信される
- **投稿が完了したら画像は削除してよい**。Instagram はコンテナ作成時に自分のサーバーへ取り込むため、以後こちらのファイルは不要
- 溜まったら古いものから消す（リポジトリを画像で膨らませない）

## 注意

- **JPEG のみ**。Instagram API は PNG を受け付けない
- ここに置いたものは URL を知っていれば誰でも見られる。**個人情報・未公開情報を含む画像は置かない**

## 関連

- 生成・投稿は `~/.claude/skills/youtube-to-infographic/` から行う
- 投稿スクリプト: `scripts/ig_client.py`
