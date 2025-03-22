### オプション

- `-h, --help`  
  ヘルプテキストを表示して終了

- `--version`  
  プログラムのバージョンを表示して終了

- `-U, --update`  
  このプログラムを最新バージョンに更新

- `--no-update`  
  更新チェックを行わない（デフォルト）

- `--update-to [CHANNEL]@[TAG]`  
  特定のバージョンにアップグレード／ダウングレードします。  
  `CHANNEL`はリポジトリでも指定可能です。  
  `CHANNEL`と`TAG`は省略するとそれぞれ「stable」と「latest」がデフォルトとなります。  
  詳細は「UPDATE」を参照。サポートされているチャンネル：`stable`, `nightly`, `master`

- `-i, --ignore-errors`  
  ダウンロードおよび後処理エラーを無視します。  
  後処理が失敗してもダウンロードは成功と見なされます

- `--no-abort-on-error`  
  ダウンロードエラーが発生した場合、次の動画をダウンロードし続けます。  
  例：プレイリスト内の利用不可な動画をスキップ（デフォルト）

- `--abort-on-error`  
  エラーが発生した場合、それ以降の動画のダウンロードを中止します（エイリアス: `--no-ignore-errors`）

- `--dump-user-agent`  
  現在のユーザーエージェントを表示して終了

- `--list-extractors`  
  サポートされている全てのエクストラクターを表示して終了

- `--extractor-descriptions`  
  サポートされている全てのエクストラクターの説明を表示して終了

- `--use-extractors NAMES`  
  使用するエクストラクター名をカンマ区切りで指定します。  
  正規表現や「all」、「default」、「end」（URL末尾一致）も使用可能。  
  例：`--ies "holodex.*,end,youtube"`。  
  名前の前に`-`を付けることで除外できます。  
  例：`--ies default,-generic`。  
  エクストラクター名のリストは`--list-extractors`で確認できます。（エイリアス: `--ies`）

- `--default-search PREFIX`  
  URLが未指定の場合に使用する検索プレフィックスを設定します。  
  例：`"gvsearch2:python"`は「python」でGoogle動画から2本をダウンロードします。  
  プレフィックス「auto」を使うと、yt-dlpが推測します（`auto_warning`で推測時に警告）。  
  `error`を指定するとエラーになります。デフォルト値「fixup_error」はURLの修正を試みますが、修正できない場合はエラーを出します。

- `--ignore-config`  
  `--config-locations`で指定された設定ファイル以外の設定ファイルを読み込まないようにします。  
  後方互換性のため、このオプションがシステム設定ファイル内にある場合、ユーザー設定は読み込まれません。（エイリアス: `--no-config`）

- `--no-config-locations`  
  カスタム設定ファイルを読み込まない（デフォルト）。  
  設定ファイル内で指定された`--config-locations`は無視されます。

- `--config-locations PATH`  
  メイン設定ファイルの場所。  
  設定ファイルのパスまたはそのディレクトリを指定します（`-`は標準入力）。  
  複数回使用可能で、他の設定ファイル内でも使用できます。

- `--plugin-dirs PATH`  
  プラグインを検索する追加ディレクトリのパス。  
  複数回指定可能。`default`を指定するとデフォルトのプラグインディレクトリを検索します（デフォルト）。

- `--no-plugin-dirs`  
  プラグインディレクトリをクリアします。デフォルトや前回指定した`--plugin-dirs`も含まれます。

- `--flat-playlist`  
  プレイリストのURL結果エントリを抽出しません。一部のエントリのメタデータが欠落する可能性があり、ダウンロードがスキップされることがあります。

- `--no-flat-playlist`  
  プレイリストの動画を完全に抽出します（デフォルト）。

- `--live-from-start`  
  ライブストリームを開始時からダウンロードします。  
  現在、YouTubeのみでサポートされています（実験的機能）。

- `--no-live-from-start`  
  ライブストリームを現在の時刻からダウンロードします（デフォルト）。

- `--wait-for-video MIN[-MAX]`  
  予定されたストリームが利用可能になるまで待機します。  
  最小（または範囲）の待機時間を指定します。

- `--no-wait-for-video`  
  予定されたストリームを待機せずにダウンロードを行います（デフォルト）。

- `--mark-watched`  
  動画を視聴済みとしてマークします（`--simulate`でも）。

- `--no-mark-watched`  
  動画を視聴済みとしてマークしません（デフォルト）。

- `--color [STREAM:]POLICY`  
  出力に色コードを出力するかどうかを指定します。  
  `STREAM`（stdoutまたはstderr）を指定して設定を適用できます。  
  値は「always」、「auto」（デフォルト）、「never」、「no_color」などがあります。  
  「auto-tty」または「no_color-tty」を指定すると、ターミナルのサポートに基づいて自動で判断されます。  
  複数回使用可能。

- `--compat-options OPTS`  
  youtube-dlやyoutube-dlcの設定と互換性を保つためのオプション。  
  yt-dlpで行った変更を元に戻すことができます。「Differences in default behavior」を参照。

- `--alias ALIASES OPTIONS`  
  オプション文字列にエイリアスを作成します。エイリアスは「--」で始まります。  
  引数はPythonの文字列フォーマットに従って解析されます。  
  例：`--alias get-audio,-X "-S=aext:{0},abr -x --audio-format {0}"`  
  これにより、`--get-audio`と`-X`が作成され、引数`ARG0`を受け取ると`-S=aext:ARG0,abr -x --audio-format ARG0`に展開されます。  
  定義されたエイリアスは`--help`でリストされます。エイリアスオプションはさらにエイリアスをトリガーすることがあるので、再帰的なオプションを避けるように注意してください。  
  各エイリアスは最大100回までトリガーされます。このオプションは複数回使用可能です。
