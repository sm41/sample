<!-- # qwerty -->

### General Options

- `-h, --help`<br>
  ヘルプテキストを表示して終了

- `--version`<br>
  プログラムのバージョンを表示して終了

- `-U, --update`<br>
  このプログラムを最新バージョンに更新

- `--no-update`<br>
  更新チェックを行わない（デフォルト）

- `--update-to [CHANNEL]@[TAG]`<br>
  特定のバージョンにアップグレード／ダウングレードします。<br>
  `CHANNEL`はリポジトリでも指定可能です。<br>
  `CHANNEL`と`TAG`は省略するとそれぞれ「stable」と「latest」がデフォルトとなります。<br>
  詳細は「UPDATE」を参照。サポートされているチャンネル：`stable`, `nightly`, `master`<br>

- `-i, --ignore-errors`<br>
  ダウンロードおよび後処理エラーを無視します。<br>
  後処理が失敗してもダウンロードは成功と見なされます

- `--no-abort-on-error`<br>
  ダウンロードエラーが発生した場合、次の動画をダウンロードし続けます。<br>
  例：プレイリスト内の利用不可な動画をスキップ（デフォルト）

- `--abort-on-error`<br>
  エラーが発生した場合、それ以降の動画のダウンロードを中止します（エイリアス: `--no-ignore-errors`）

- `--dump-user-agent`<br>
  現在のユーザーエージェントを表示して終了

- `--list-extractors`<br>
  サポートされている全てのエクストラクターを表示して終了

- `--extractor-descriptions`<br>
  サポートされている全てのエクストラクターの説明を表示して終了

- `--use-extractors NAMES`<br>
  使用するエクストラクター名をカンマ区切りで指定します。<br>
  正規表現や「all」、「default」、「end」（URL末尾一致）も使用可能。<br>
  例：`--ies "holodex.*,end,youtube"`。<br>
  名前の前に`-`を付けることで除外できます。<br>
  例：`--ies default,-generic`。<br>
  エクストラクター名のリストは`--list-extractors`で確認できます。（エイリアス: `--ies`）

- `--default-search PREFIX`<br>
  URLが未指定の場合に使用する検索プレフィックスを設定します。<br>
  例：`"gvsearch2:python"`は「python」でGoogle動画から2本をダウンロードします。<br>
  プレフィックス「auto」を使うと、yt-dlpが推測します（`auto_warning`で推測時に警告）。<br>
  `error`を指定するとエラーになります。デフォルト値「fixup_error」はURLの修正を試みますが、修正できない場合はエラーを出します。<br>

- `--ignore-config`<br>
  `--config-locations`で指定された設定ファイル以外の設定ファイルを読み込まないようにします。<br>
  後方互換性のため、このオプションがシステム設定ファイル内にある場合、ユーザー設定は読み込まれません。（エイリアス: `--no-config`）

- `--no-config-locations`<br>
  カスタム設定ファイルを読み込まない（デフォルト）。<br>
  設定ファイル内で指定された`--config-locations`は無視されます。<br>

- `--config-locations PATH`<br>
  メイン設定ファイルの場所。<br>
  設定ファイルのパスまたはそのディレクトリを指定します（`-`は標準入力）。<br>
  複数回使用可能で、他の設定ファイル内でも使用できます。<br>

- `--plugin-dirs PATH`<br>
  プラグインを検索する追加ディレクトリのパス。<br>
  複数回指定可能。`default`を指定するとデフォルトのプラグインディレクトリを検索します（デフォルト）。<br>

- `--no-plugin-dirs`<br>
  プラグインディレクトリをクリアします。デフォルトや前回指定した`--plugin-dirs`も含まれます。<br>

- `--flat-playlist`<br>
  プレイリストのURL結果エントリを抽出しません。一部のエントリのメタデータが欠落する可能性があり、ダウンロードがスキップされることがあります。<br>

- `--no-flat-playlist`<br>
  プレイリストの動画を完全に抽出します（デフォルト）。<br>

- `--live-from-start`<br>
  ライブストリームを開始時からダウンロードします。<br>
  現在、YouTubeのみでサポートされています（実験的機能）。<br>

- `--no-live-from-start`<br>
  ライブストリームを現在の時刻からダウンロードします（デフォルト）。<br>

- `--wait-for-video MIN[-MAX]`<br>
  予定されたストリームが利用可能になるまで待機します。<br>
  最小（または範囲）の待機時間を指定します。<br>

- `--no-wait-for-video`<br>
  予定されたストリームを待機せずにダウンロードを行います（デフォルト）。<br>

- `--mark-watched`<br>
  動画を視聴済みとしてマークします（`--simulate`でも）。<br>

- `--no-mark-watched`<br>
  動画を視聴済みとしてマークしません（デフォルト）。<br>

- `--color [STREAM:]POLICY`<br>
  出力に色コードを出力するかどうかを指定します。<br>
  `STREAM`（stdoutまたはstderr）を指定して設定を適用できます。<br>
  値は「always」、「auto」（デフォルト）、「never」、「no_color」などがあります。<br>
  「auto-tty」または「no_color-tty」を指定すると、ターミナルのサポートに基づいて自動で判断されます。<br>
  複数回使用可能。<br>

- `--compat-options OPTS`<br>
  youtube-dlやyoutube-dlcの設定と互換性を保つためのオプション。<br>
  yt-dlpで行った変更を元に戻すことができます。「Differences in default behavior」を参照。<br>

- `--alias ALIASES OPTIONS`<br>
  オプション文字列にエイリアスを作成します。エイリアスは「--」で始まります。<br>
  引数はPythonの文字列フォーマットに従って解析されます。<br>
  例：`--alias get-audio,-X "-S=aext:{0},abr -x --audio-format {0}"`<br>
  これにより、`--get-audio`と`-X`が作成され、引数`ARG0`を受け取ると`-S=aext:ARG0,abr -x --audio-format ARG0`に展開されます。<br>
  定義されたエイリアスは`--help`でリストされます。エイリアスオプションはさらにエイリアスをトリガーすることがあるので、再帰的なオプションを避けるように注意してください。<br>
  各エイリアスは最大100回までトリガーされます。このオプションは複数回使用可能です。<br>

<br>

### Network Options

- `--proxy URL`<br>
  指定したHTTP/HTTPS/SOCKSプロキシを使用します。<br>
  SOCKSプロキシを有効にするには、適切なスキームを指定します。<br>
  例：`socks5://user:pass@127.0.0.1:1080/`。<br>
  直接接続するには空文字列`--proxy ""`を渡します。<br>

- `--socket-timeout SECONDS`<br>
  諦める前に待機する時間（秒単位）

- `--source-address IP`<br>
  バインドするクライアント側のIPアドレスを指定します。<br>

- `--impersonate CLIENT[:OS]`<br>
  リクエストに対して擬似的にクライアントを指定します。<br>
  例：`chrome`, `chrome-110`, `chrome:windows-10`。<br>
  `--impersonate=""`を指定すると、任意のクライアントを擬似的に指定します。<br>
  注意：全てのリクエストで擬似クライアントを強制すると、ダウンロード速度や安定性に悪影響を及ぼす可能性があります。<br>

- `--list-impersonate-targets`<br>
  擬似クライアントとして使用可能なクライアントのリストを表示します。<br>

- `-4, --force-ipv4`<br>
  すべての接続をIPv4経由で行います。<br>

- `-6, --force-ipv6`<br>
  すべての接続をIPv6経由で行います。<br>

- `--enable-file-urls`<br>
  `file://` URLを有効にします。<br>
  セキュリティ上の理由から、デフォルトでは無効になっています。<br>

### Geo-restriction

- `--geo-verification-proxy URL`<br>
  一部の地域制限されたサイトのIPアドレスを確認するために、このプロキシを使用します。<br>
  実際のダウンロードには、`--proxy`で指定されたデフォルトのプロキシ（またはオプションが指定されていない場合はプロキシなし）が使用されます。<br>

- `--xff VALUE`<br>
  地理的制限を回避するために、`X-Forwarded-For` HTTPヘッダーをどのように偽装するかを指定します。<br>
  値は以下のいずれかです：
  - `"default"`（有効な場合のみ使用）
  - `"never"`<br>
  - CIDR表記でのIPブロック
  - 2文字のISO 3166-2国コード

<br>

### Video Selection

- `-I, --playlist-items ITEM_SPEC`<br>
  ダウンロードするアイテムのプレイリストインデックスをカンマ区切りで指定します。<br>
  範囲指定には`[START]:[STOP][:STEP]`を使用できます。<br>
  後方互換性のため、`START-STOP`形式もサポートされています。<br>
  右からカウントするには負のインデックスを使用し、逆順でダウンロードするには負の`STEP`を使用します。<br>
  例：`-I 1:3,7,-5::2`をプレイリストのサイズ15に使用すると、インデックス1、2、3、7、11、13、15のアイテムがダウンロードされます。<br>

- `--min-filesize SIZE`<br>
  ファイルサイズが指定したサイズより小さい場合、ダウンロードを中止します。<br>
  例：50kや44.6Mなどの形式で指定します。<br>

- `--max-filesize SIZE`<br>
  ファイルサイズが指定したサイズより大きい場合、ダウンロードを中止します。<br>
  例：50kや44.6Mなどの形式で指定します。<br>

- `--date DATE`<br>
  この日付にアップロードされた動画のみをダウンロードします。<br>
  日付は「YYYYMMDD」形式または、`[now|today|yesterday][-N[day|week|month|year]]`の形式で指定できます。<br>
  例：`--date today-2weeks`は、2週間前の同日にアップロードされた動画のみをダウンロードします。<br>

- `--datebefore DATE`<br>
  この日付以前にアップロードされた動画のみをダウンロードします。<br>
  日付形式は`--date`と同じです。<br>

- `--dateafter DATE`<br>
  この日付以降にアップロードされた動画のみをダウンロードします。<br>
  日付形式は`--date`と同じです。<br>

- `--match-filters FILTER`<br>
  動画フィルター。<br>
  任意の「OUTPUT TEMPLATE」フィールドを数値や文字列と比較できます。<br>
  フィルタリングの条件として、フィールドが存在する場合はそのフィールド名を指定し、`!field`でフィールドが存在しない場合を指定できます。<br>
  複数の条件をチェックするには`&`を使用します。<br>
  例：`--match-filters !is_live --match-filters "like_count>?100 & description~='(?i)\bcats \& dogs\b'"`は、ライブでない動画、または「like_count」が100以上の動画で、「cats & dogs」というフレーズを含む説明の動画のみを対象とします。<br>
  `--match-filters -`を使うと、ダウンロードするかどうかをインタラクティブに確認できます。<br>

- `--no-match-filters`<br>
  フィルタを使用しません（デフォルト）。<br>

- `--break-match-filters FILTER`<br>
  `--match-filters`と同じですが、動画が拒否された場合、ダウンロードプロセスを停止します。<br>

- `--no-break-match-filters`<br>
  `--break-match-filters`を使用しません（デフォルト）。<br>

- `--no-playlist`<br>
  プレイリストが含まれるURLの場合、動画のみをダウンロードします。<br>

- `--yes-playlist`<br>
  プレイリストが含まれるURLの場合、プレイリストをダウンロードします。<br>

- `--age-limit YEARS`<br>
  指定した年齢制限に適した動画のみをダウンロードします。<br>

- `--download-archive FILE`<br>
  アーカイブファイルに記載されていない動画のみをダウンロードします。<br>
  ダウンロードした動画のIDをアーカイブファイルに記録します。<br>

- `--no-download-archive`<br>
  アーカイブファイルを使用しません（デフォルト）。<br>

- `--max-downloads NUMBER`<br>
  指定した数だけファイルをダウンロードしたら中止します。<br>

- `--break-on-existing`<br>
  アーカイブファイルに存在するファイルを見つけた時点でダウンロードプロセスを停止します。<br>

- `--no-break-on-existing`<br>
  アーカイブファイルに存在するファイルを見つけてもダウンロードプロセスを停止しません（デフォルト）。<br>

- `--break-per-input`<br>
  `--max-downloads`, `--break-on-existing`, `--break-match-filters`, および自動番号付けを各入力URLごとにリセットします。<br>

- `--no-break-per-input`<br>
  `--break-on-existing`などのオプションは、ダウンロードキュー全体に影響を与えます。<br>

- `--skip-playlist-after-errors N`<br>
  プレイリストでエラーが発生した場合、N回の失敗まで許容し、それ以降はプレイリストの残りの部分をスキップします。<br>

<br>

### Download Options

- `-N, --concurrent-fragments N`<br>
  DASH/hlsnativeビデオのフラグメントを並行してダウンロードする数（デフォルトは1）。<br>

- `-r, --limit-rate RATE`<br>
  最大ダウンロード速度（バイト/秒）。例：50Kや4.2M。<br>

- `--throttled-rate RATE`<br>
  ダウンロード速度がこの値以下の場合、帯域制限がかかっていると見なし、ビデオデータを再抽出します。例：100K。<br>

- `-R, --retries RETRIES`<br>
  再試行回数（デフォルトは10回）、または「infinite」。<br>

- `--file-access-retries RETRIES`<br>
  ファイルアクセスエラー時の再試行回数（デフォルトは3回）、または「infinite」。<br>

- `--fragment-retries RETRIES`<br>
  フラグメントの再試行回数（デフォルトは10回）、または「infinite」（DASH、hlsnative、ISM）。<br>

- `--retry-sleep [TYPE:]EXPR`<br>
  再試行の間に睡眠する時間（秒単位）。オプションで再試行タイプ（http（デフォルト）、fragment、file_access、extractor）を指定し、その再試行に適用できます。EXPRには数値、線形（`linear=START[:END[:STEP=1]]`）、または指数（`exp=START[:END[:BASE=2]]`）を使用できます。このオプションは複数回使用して、異なる再試行タイプに対して異なる睡眠時間を設定できます。<br>

- `--skip-unavailable-fragments`<br>
  DASH、hlsnative、ISMダウンロードで利用できないフラグメントをスキップします（デフォルト）。<br>
  （エイリアス：`--no-abort-on-unavailable-fragments`）

- `--abort-on-unavailable-fragments`<br>
  フラグメントが利用できない場合、ダウンロードを中止します。<br>
  （エイリアス：`--no-skip-unavailable-fragments`）

- `--keep-fragments`<br>
  ダウンロードが完了した後、ダウンロードしたフラグメントをディスクに保持します。<br>

- `--no-keep-fragments`<br>
  ダウンロードが完了した後、ダウンロードしたフラグメントを削除します（デフォルト）。<br>

- `--buffer-size SIZE`<br>
  ダウンロードバッファのサイズ。例：1024または16K（デフォルトは1024）。<br>

- `--resize-buffer`<br>
  バッファサイズが自動的に調整されます（デフォルトの`--buffer-size`から開始）。<br>

- `--no-resize-buffer`<br>
  バッファサイズを自動的に調整しません。<br>

- `--http-chunk-size SIZE`<br>
  チャンクベースのHTTPダウンロードのチャンクサイズ。例：10485760または10M（デフォルトは無効）。<br>
  ウェブサーバーによる帯域制限を回避するために役立つ場合があります（実験的）。<br>

- `--playlist-random`<br>
  プレイリストの動画をランダムな順序でダウンロードします。<br>

- `--lazy-playlist`<br>
  プレイリストのエントリを受信する際に処理します。これにより`n_entries`、`--playlist-random`、`--playlist-reverse`が無効になります。<br>

- `--no-lazy-playlist`<br>
  プレイリストのすべての動画を解析した後にのみ処理します（デフォルト）。<br>

- `--xattr-set-filesize`<br>
  ファイルのx属性`ytdl.filesize`に予想されるファイルサイズを設定します。<br>

- `--hls-use-mpegts`<br>
  HLSビデオ用にmpegtsコンテナを使用します。これにより、いくつかのプレーヤーでビデオをダウンロード中に再生できるようになり、ダウンロードが中断された場合のファイル破損のリスクが減少します。<br>
  これはライブストリームのダウンロード時にデフォルトで有効です。<br>

- `--no-hls-use-mpegts`<br>
  HLSビデオでmpegtsコンテナを使用しません。ライブストリーム以外のダウンロード時はこれがデフォルトです。<br>

- `--download-sections REGEX`<br>
  正規表現に一致するチャプターのみをダウンロードします。<br>
  `*`プレフィックスを使うと、チャプターではなく時間範囲を指定できます。負のタイムスタンプは終了から計算されます。<br>
  `*from-url`を使うと、URLから抽出した`start_time`と`end_time`の間をダウンロードできます。<br>
  このオプションは複数回使用して複数のセクションをダウンロードできます。例：`--download-sections "*10:15-inf"`、`--download-sections "intro"`。<br>

- `--downloader [PROTO:]NAME`<br>
  使用する外部ダウンローダーの名前またはパス。プロトコル（http、ftp、m3u8、dash、rstp、rtmp、mms）を指定して、それに対応するダウンローダーを指定できます。<br>
  現在サポートされているダウンローダー：`native`、`aria2c`、`avconv`、`axel`、`curl`、`ffmpeg`、`httpie`、`wget`。<br>
  このオプションは、異なるプロトコルに対して異なるダウンローダーを設定するために複数回使用できます。例：`--downloader aria2c --downloader "dash,m3u8:native"`は、http/ftpダウンロードにaria2cを、dash/m3u8ダウンロードにnativeダウンローダーを使用します。<br>
  （エイリアス：`--external-downloader`）

- `--downloader-args NAME:ARGS`<br>
  外部ダウンローダーに渡す引数を指定します。ダウンローダー名と引数をコロン`:`で区切って指定します。<br>
  `ffmpeg`には、`--postprocessor-args`と同じ構文を使って異なる位置に引数を渡すことができます。<br>
  このオプションは、異なるダウンローダーに異なる引数を渡すために複数回使用できます。<br>
  （エイリアス：`--external-downloader-args`）

<br>

### Filesystem Options

- `-a, --batch-file FILE`<br>
  ダウンロードするURLを含むファイル（"-"で標準入力）。各行に1つのURLを記載します。`#`、`;`、または`]`で始まる行はコメントとして扱われ、無視されます。<br>

- `--no-batch-file`<br>
  バッチファイルからURLを読み込まない（デフォルト）。<br>

- `-P, --paths [TYPES:]PATH`<br>
  ファイルをダウンロードするパスを指定します。ファイルの種類とパスをコロン（`:`）で区切って指定します。`--output`と同じTYPESがサポートされます。さらに、「home」（デフォルト）や「temp」パスを指定することもできます。すべての中間ファイルはまずtempパスにダウンロードされ、ダウンロードが完了した後に最終ファイルがhomeパスに移動されます。このオプションは、`--output`が絶対パスの場合は無視されます。<br>

- `-o, --output [TYPES:]TEMPLATE`<br>
  出力ファイル名のテンプレート。詳細は「OUTPUT TEMPLATE」を参照してください。<br>

- `--output-na-placeholder TEXT`<br>
  `--output`に指定されたフィールドが利用できない場合のプレースホルダ（デフォルトは"NA"）。<br>

- `--restrict-filenames`<br>
  ファイル名をASCII文字のみに制限し、`&`やスペースをファイル名に含めないようにします。<br>

- `--no-restrict-filenames`<br>
  ファイル名にUnicode文字、`&`、スペースを許可します（デフォルト）。<br>

- `--windows-filenames`<br>
  ファイル名をWindows互換に強制します。<br>

- `--no-windows-filenames`<br>
  ファイル名を最小限にサニタイズします。<br>

- `--trim-filenames LENGTH`<br>
  ファイル名の長さ（拡張子を除く）を指定した文字数に制限します。<br>

- `-w, --no-overwrites`<br>
  既存のファイルを上書きしません。<br>

- `--force-overwrites`<br>
  すべてのビデオとメタデータファイルを上書きします。このオプションには`--no-continue`も含まれます。<br>

- `--no-force-overwrites`<br>
  ビデオは上書きせず、関連するファイルのみを上書きします（デフォルト）。<br>

- `-c, --continue`<br>
  部分的にダウンロードされたファイルやフラグメントを再開します（デフォルト）。<br>

- `--no-continue`<br>
  部分的にダウンロードされたフラグメントを再開しません。ファイルがフラグメントでない場合、ダウンロードは最初からやり直されます。<br>

- `--part`<br>
  `.part`ファイルを使用して、出力ファイルに直接書き込まずにダウンロードします（デフォルト）。<br>

- `--no-part`<br>
  `.part`ファイルを使用せず、出力ファイルに直接書き込みます。<br>

- `--mtime`<br>
  Last-modifiedヘッダーを使用してファイルの変更時刻を設定します（デフォルト）。<br>

- `--no-mtime`<br>
  Last-modifiedヘッダーを使用してファイルの変更時刻を設定しません。<br>

- `--write-description`<br>
  ビデオの説明を`.description`ファイルに書き込みます。<br>

- `--no-write-description`<br>
  ビデオの説明を書き込みません（デフォルト）。<br>

- `--write-info-json`<br>
  ビデオのメタデータを`.info.json`ファイルに書き込みます（これには個人情報が含まれる場合があります）。<br>

- `--no-write-info-json`<br>
  ビデオのメタデータを書き込みません（デフォルト）。<br>

- `--write-playlist-metafiles`<br>
  `--write-info-json`や`--write-description`などを使用する際に、ビデオメタデータに加えてプレイリストメタデータも書き込みます（デフォルト）。<br>

- `--no-write-playlist-metafiles`<br>
  `--write-info-json`や`--write-description`などを使用する際に、プレイリストメタデータを書き込みません。<br>

- `--clean-info-json`<br>
  `infojson`からファイル名などの内部メタデータを削除します（デフォルト）。<br>

- `--no-clean-info-json`<br>
  `infojson`にすべてのフィールドを記録します。<br>

- `--write-comments`<br>
  ビデオのコメントを取得し、`infojson`に書き込みます。このオプションがなくても、抽出が早い場合はコメントが取得されます。<br>
  （エイリアス：`--get-comments`）

- `--no-write-comments`<br>
  抽出が早い場合を除き、ビデオのコメントは取得しません。<br>
  （エイリアス：`--no-get-comments`）

- `--load-info-json FILE`<br>
  ビデオ情報を含むJSONファイル（`--write-info-json`オプションで作成）を読み込みます。<br>

- `--cookies FILE`<br>
  クッキーを読み込むためのNetscape形式のファイル。クッキージャーにダンプも可能です。<br>

- `--no-cookies`<br>
  ファイルからクッキーを読み込んだりダンプしたりしません（デフォルト）。<br>

- `--cookies-from-browser BROWSER[+KEYRING][:PROFILE][::CONTAINER]`<br>
  クッキーを読み込むためのブラウザ名。サポートされているブラウザは、brave、chrome、chromium、edge、firefox、opera、safari、vivaldi、whaleです。オプションで、ChromiumクッキーをLinuxで復号化するためのKEYRING、クッキーを読み込むPROFILE名/パス、Firefoxの場合はCONTAINER名を指定できます（デフォルトでは最新アクセスされたプロフィールのすべてのコンテナを使用）。<br>

- `--no-cookies-from-browser`<br>
  ブラウザからクッキーを読み込まない（デフォルト）。<br>

- `--cache-dir DIR`<br>
  yt-dlpがダウンロードした情報（クライアントIDや署名など）を永続的に保存するファイルシステム上の場所。デフォルトは`${XDG_CACHE_HOME}/yt-dlp`です。<br>

- `--no-cache-dir`<br>
  ファイルシステムキャッシュを無効にします。<br>

- `--rm-cache-dir`<br>
  すべてのファイルシステムキャッシュファイルを削除します。<br>

<br>

### Thumbnail Options

- `--write-thumbnail`<br>
  サムネイル画像をディスクに書き込みます。<br>

- `--no-write-thumbnail`<br>
  サムネイル画像をディスクに書き込まない（デフォルト）。<br>

- `--write-all-thumbnails`<br>
  すべてのサムネイル画像フォーマットをディスクに書き込みます。<br>

- `--list-thumbnails`<br>
  各ビデオの利用可能なサムネイルをリスト表示します。<br>
  `--no-simulate` オプションを使用しない場合、シミュレートされます。<br>

<br>

### Internet Shortcut Options

- `--write-link`<br>
  現在のプラットフォームに応じたインターネットショートカットファイルを作成します（.url, .webloc, または .desktop）。URLはOSによってキャッシュされる場合があります。<br>

- `--write-url-link`<br>
  .url形式のWindowsインターネットショートカットを作成します。OSはファイルパスに基づいてURLをキャッシュします。<br>

- `--write-webloc-link`<br>
  .webloc形式のmacOSインターネットショートカットを作成します。<br>

- `--write-desktop-link`<br>
  .desktop形式のLinuxインターネットショートカットを作成します。<br>

<br>

### Verbosity and Simulation Options

- `-q, --quiet`<br>
  クワイエットモードを有効にします。`--verbose`オプションと併用した場合、ログは標準エラー出力に表示されます。<br>

- `--no-quiet`<br>
  クワイエットモードを無効にします（デフォルト）。<br>

- `--no-warnings`<br>
  警告を無視します。<br>

- `-s, --simulate`<br>
  動画をダウンロードせず、ディスクに何も書き込まないシミュレーションモードを有効にします。<br>

- `--no-simulate`<br>
  動画をダウンロードし、オプションの表示やリストが使用されても実際にダウンロードを行います。<br>

- `--ignore-no-formats-error`<br>
  "No video formats" エラーを無視します。実際にダウンロード可能な動画がない場合でも、メタデータの抽出ができます（実験的機能）。<br>

- `--no-ignore-no-formats-error`<br>
  ダウンロード可能な動画フォーマットが見つからない場合、エラーを発生させます（デフォルト）。<br>

- `--skip-download`<br>
  動画をダウンロードせず、関連するファイルだけを書き込みます（別名: `--no-download`）。<br>

### 出力に関する設定

- `-O, --print [WHEN:]TEMPLATE`<br>
  指定したフィールド名または出力テンプレートを画面に表示します。`WHEN`をオプションとして指定し、いつ表示するかを設定できます。デフォルトは「video」です。複数回使用できます。<br>

- `--print-to-file [WHEN:]TEMPLATE FILE`<br>
  指定したテンプレートをファイルに追加します。`WHEN` と `TEMPLATE` の値は `--print` と同じです。ファイルのパスは出力テンプレートと同じ構文を使用します。複数回使用できます。<br>

- `-j, --dump-json`<br>
  クワイエットモードで実行し、各動画のJSON情報を表示します。`--no-simulate`が使用されない限りシミュレートモードで動作します。<br>

- `-J, --dump-single-json`<br>
  クワイエットモードで実行し、各URLまたは`infojson`のJSON情報を表示します。シミュレートモードで動作します。URLがプレイリストを指す場合、プレイリストの全情報が一行で出力されます。<br>

- `--force-write-archive`<br>
  エラーが発生しない限り、ダウンロードアーカイブのエントリを強制的に書き込みます。シミュレーションオプション（`-s`など）を使用してもアーカイブへの書き込みが行われます（別名: `--force-download-archive`）。<br>

- `--newline`<br>
  進行状況バーを新しい行で表示します。<br>

- `--no-progress`<br>
  進行状況バーを表示しません。<br>

- `--progress`<br>
  クワイエットモードでも進行状況バーを表示します。<br>

- `--console-title`<br>
  コンソールのタイトルバーに進行状況を表示します。<br>

- `--progress-template [TYPES:]TEMPLATE`<br>
  進行状況の出力テンプレートを指定します。オプションで `download:`（デフォルト）、`download-title:`（コンソールタイトル）、`postprocess:` または `postprocess-title:`を指定できます。<br>

- `--progress-delta SECONDS`<br>
  進行状況の出力間隔を秒単位で設定します（デフォルトは 0）。<br>

- `-v, --verbose`<br>
  各種デバッグ情報を表示します。<br>

- `--dump-pages`<br>
  ダウンロードしたページをbase64エンコードして表示し、問題をデバッグします（非常に詳細な表示）。<br>

- `--write-pages`<br>
  ダウンロードした中間ページを現在のディレクトリにファイルとして書き込み、問題をデバッグします。<br>

- `--print-traffic`<br>
  送信および受信したHTTPトラフィックを表示します。<br>
