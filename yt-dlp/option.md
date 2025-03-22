# qwerty

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
  特定のバージョンにアップグレード／ダウングレードします。
  `CHANNEL`はリポジトリでも指定可能です。
  `CHANNEL`と`TAG`は省略するとそれぞれ「stable」と「latest」がデフォルトとなります。
  詳細は「UPDATE」を参照。サポートされているチャンネル：`stable`, `nightly`, `master`<br>

- `-i, --ignore-errors`<br>
  ダウンロードおよび後処理エラーを無視します。
  後処理が失敗してもダウンロードは成功と見なされます

- `--no-abort-on-error`<br>
  ダウンロードエラーが発生した場合、次の動画をダウンロードし続けます。
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
  使用するエクストラクター名をカンマ区切りで指定します。
  正規表現や「all」、「default」、「end」（URL末尾一致）も使用可能。
  例：`--ies "holodex.*,end,youtube"`。
  名前の前に`-`を付けることで除外できます。
  例：`--ies default,-generic`。
  エクストラクター名のリストは`--list-extractors`で確認できます。（エイリアス: `--ies`）

- `--default-search PREFIX`<br>
  URLが未指定の場合に使用する検索プレフィックスを設定します。
  例：`"gvsearch2:python"`は「python」でGoogle動画から2本をダウンロードします。
  プレフィックス「auto」を使うと、yt-dlpが推測します（`auto_warning`で推測時に警告）。
  `error`を指定するとエラーになります。デフォルト値「fixup_error」はURLの修正を試みますが、修正できない場合はエラーを出します。

- `--ignore-config`<br>
  `--config-locations`で指定された設定ファイル以外の設定ファイルを読み込まないようにします。
  後方互換性のため、このオプションがシステム設定ファイル内にある場合、ユーザー設定は読み込まれません。（エイリアス: `--no-config`）

- `--no-config-locations`<br>
  カスタム設定ファイルを読み込まない（デフォルト）。
  設定ファイル内で指定された`--config-locations`は無視されます。

- `--config-locations PATH`<br>
  メイン設定ファイルの場所。
  設定ファイルのパスまたはそのディレクトリを指定します（`-`は標準入力）。
  複数回使用可能で、他の設定ファイル内でも使用できます。

- `--plugin-dirs PATH`<br>
  プラグインを検索する追加ディレクトリのパス。
  複数回指定可能。`default`を指定するとデフォルトのプラグインディレクトリを検索します（デフォルト）。

- `--no-plugin-dirs`<br>
  プラグインディレクトリをクリアします。デフォルトや前回指定した`--plugin-dirs`も含まれます。

- `--flat-playlist`<br>
  プレイリストのURL結果エントリを抽出しません。一部のエントリのメタデータが欠落する可能性があり、ダウンロードがスキップされることがあります。

- `--no-flat-playlist`<br>
  プレイリストの動画を完全に抽出します（デフォルト）。

- `--live-from-start`<br>
  ライブストリームを開始時からダウンロードします。
  現在、YouTubeのみでサポートされています（実験的機能）。

- `--no-live-from-start`<br>
  ライブストリームを現在の時刻からダウンロードします（デフォルト）。

- `--wait-for-video MIN[-MAX]`<br>
  予定されたストリームが利用可能になるまで待機します。
  最小（または範囲）の待機時間を指定します。

- `--no-wait-for-video`<br>
  予定されたストリームを待機せずにダウンロードを行います（デフォルト）。

- `--mark-watched`<br>
  動画を視聴済みとしてマークします（`--simulate`でも）。

- `--no-mark-watched`<br>
  動画を視聴済みとしてマークしません（デフォルト）。

- `--color [STREAM:]POLICY`<br>
  出力に色コードを出力するかどうかを指定します。
  `STREAM`（stdoutまたはstderr）を指定して設定を適用できます。
  値は「always」、「auto」（デフォルト）、「never」、「no_color」などがあります。
  「auto-tty」または「no_color-tty」を指定すると、ターミナルのサポートに基づいて自動で判断されます。
  複数回使用可能。

- `--compat-options OPTS`<br>
  youtube-dlやyoutube-dlcの設定と互換性を保つためのオプション。
  yt-dlpで行った変更を元に戻すことができます。「Differences in default behavior」を参照。

- `--alias ALIASES OPTIONS`<br>
  オプション文字列にエイリアスを作成します。エイリアスは「--」で始まります。
  引数はPythonの文字列フォーマットに従って解析されます。
  例：`--alias get-audio,-X "-S=aext:{0},abr -x --audio-format {0}"`<br>
  これにより、`--get-audio`と`-X`が作成され、引数`ARG0`を受け取ると`-S=aext:ARG0,abr -x --audio-format ARG0`に展開されます。
  定義されたエイリアスは`--help`でリストされます。エイリアスオプションはさらにエイリアスをトリガーすることがあるので、再帰的なオプションを避けるように注意してください。
  各エイリアスは最大100回までトリガーされます。このオプションは複数回使用可能です。




  ### Network Options

- `--proxy URL`<br>
  指定したHTTP/HTTPS/SOCKSプロキシを使用します。
  SOCKSプロキシを有効にするには、適切なスキームを指定します。
  例：`socks5://user:pass@127.0.0.1:1080/`。
  直接接続するには空文字列`--proxy ""`を渡します。

- `--socket-timeout SECONDS`<br>
  諦める前に待機する時間（秒単位）

- `--source-address IP`<br>
  バインドするクライアント側のIPアドレスを指定します。

- `--impersonate CLIENT[:OS]`<br>
  リクエストに対して擬似的にクライアントを指定します。
  例：`chrome`, `chrome-110`, `chrome:windows-10`。
  `--impersonate=""`を指定すると、任意のクライアントを擬似的に指定します。
  注意：全てのリクエストで擬似クライアントを強制すると、ダウンロード速度や安定性に悪影響を及ぼす可能性があります。

- `--list-impersonate-targets`<br>
  擬似クライアントとして使用可能なクライアントのリストを表示します。

- `-4, --force-ipv4`<br>
  すべての接続をIPv4経由で行います。

- `-6, --force-ipv6`<br>
  すべての接続をIPv6経由で行います。

- `--enable-file-urls`<br>
  `file://` URLを有効にします。
  セキュリティ上の理由から、デフォルトでは無効になっています。

### Geo-restriction

- `--geo-verification-proxy URL`<br>
  一部の地域制限されたサイトのIPアドレスを確認するために、このプロキシを使用します。
  実際のダウンロードには、`--proxy`で指定されたデフォルトのプロキシ（またはオプションが指定されていない場合はプロキシなし）が使用されます。

- `--xff VALUE`<br>
  地理的制限を回避するために、`X-Forwarded-For` HTTPヘッダーをどのように偽装するかを指定します。
  値は以下のいずれかです：
  - `"default"`（有効な場合のみ使用）
  - `"never"`<br>
  - CIDR表記でのIPブロック
  - 2文字のISO 3166-2国コード



### Video Selection

- `-I, --playlist-items ITEM_SPEC`<br>
  ダウンロードするアイテムのプレイリストインデックスをカンマ区切りで指定します。
  範囲指定には`[START]:[STOP][:STEP]`を使用できます。
  後方互換性のため、`START-STOP`形式もサポートされています。
  右からカウントするには負のインデックスを使用し、逆順でダウンロードするには負の`STEP`を使用します。
  例：`-I 1:3,7,-5::2`をプレイリストのサイズ15に使用すると、インデックス1、2、3、7、11、13、15のアイテムがダウンロードされます。

- `--min-filesize SIZE`<br>
  ファイルサイズが指定したサイズより小さい場合、ダウンロードを中止します。
  例：50kや44.6Mなどの形式で指定します。

- `--max-filesize SIZE`<br>
  ファイルサイズが指定したサイズより大きい場合、ダウンロードを中止します。
  例：50kや44.6Mなどの形式で指定します。

- `--date DATE`<br>
  この日付にアップロードされた動画のみをダウンロードします。
  日付は「YYYYMMDD」形式または、`[now|today|yesterday][-N[day|week|month|year]]`の形式で指定できます。
  例：`--date today-2weeks`は、2週間前の同日にアップロードされた動画のみをダウンロードします。

- `--datebefore DATE`<br>
  この日付以前にアップロードされた動画のみをダウンロードします。
  日付形式は`--date`と同じです。

- `--dateafter DATE`<br>
  この日付以降にアップロードされた動画のみをダウンロードします。
  日付形式は`--date`と同じです。

- `--match-filters FILTER`<br>
  動画フィルター。
  任意の「OUTPUT TEMPLATE」フィールドを数値や文字列と比較できます。
  フィルタリングの条件として、フィールドが存在する場合はそのフィールド名を指定し、`!field`でフィールドが存在しない場合を指定できます。
  複数の条件をチェックするには`&`を使用します。
  例：`--match-filters !is_live --match-filters "like_count>?100 & description~='(?i)\bcats \& dogs\b'"`は、ライブでない動画、または「like_count」が100以上の動画で、「cats & dogs」というフレーズを含む説明の動画のみを対象とします。
  `--match-filters -`を使うと、ダウンロードするかどうかをインタラクティブに確認できます。

- `--no-match-filters`<br>
  フィルタを使用しません（デフォルト）。

- `--break-match-filters FILTER`<br>
  `--match-filters`と同じですが、動画が拒否された場合、ダウンロードプロセスを停止します。

- `--no-break-match-filters`<br>
  `--break-match-filters`を使用しません（デフォルト）。

- `--no-playlist`<br>
  プレイリストが含まれるURLの場合、動画のみをダウンロードします。

- `--yes-playlist`<br>
  プレイリストが含まれるURLの場合、プレイリストをダウンロードします。

- `--age-limit YEARS`<br>
  指定した年齢制限に適した動画のみをダウンロードします。

- `--download-archive FILE`<br>
  アーカイブファイルに記載されていない動画のみをダウンロードします。
  ダウンロードした動画のIDをアーカイブファイルに記録します。

- `--no-download-archive`<br>
  アーカイブファイルを使用しません（デフォルト）。

- `--max-downloads NUMBER`<br>
  指定した数だけファイルをダウンロードしたら中止します。

- `--break-on-existing`<br>
  アーカイブファイルに存在するファイルを見つけた時点でダウンロードプロセスを停止します。

- `--no-break-on-existing`<br>
  アーカイブファイルに存在するファイルを見つけてもダウンロードプロセスを停止しません（デフォルト）。

- `--break-per-input`<br>
  `--max-downloads`, `--break-on-existing`, `--break-match-filters`, および自動番号付けを各入力URLごとにリセットします。

- `--no-break-per-input`<br>
  `--break-on-existing`などのオプションは、ダウンロードキュー全体に影響を与えます。

- `--skip-playlist-after-errors N`<br>
  プレイリストでエラーが発生した場合、N回の失敗まで許容し、それ以降はプレイリストの残りの部分をスキップします。



### Download Options

- `-N, --concurrent-fragments N`<br>
  DASH/hlsnativeビデオのフラグメントを並行してダウンロードする数（デフォルトは1）。

- `-r, --limit-rate RATE`<br>
  最大ダウンロード速度（バイト/秒）。例：50Kや4.2M。

- `--throttled-rate RATE`<br>
  ダウンロード速度がこの値以下の場合、帯域制限がかかっていると見なし、ビデオデータを再抽出します。例：100K。

- `-R, --retries RETRIES`<br>
  再試行回数（デフォルトは10回）、または「infinite」。

- `--file-access-retries RETRIES`<br>
  ファイルアクセスエラー時の再試行回数（デフォルトは3回）、または「infinite」。

- `--fragment-retries RETRIES`<br>
  フラグメントの再試行回数（デフォルトは10回）、または「infinite」（DASH、hlsnative、ISM）。

- `--retry-sleep [TYPE:]EXPR`<br>
  再試行の間に睡眠する時間（秒単位）。オプションで再試行タイプ（http（デフォルト）、fragment、file_access、extractor）を指定し、その再試行に適用できます。EXPRには数値、線形（`linear=START[:END[:STEP=1]]`）、または指数（`exp=START[:END[:BASE=2]]`）を使用できます。このオプションは複数回使用して、異なる再試行タイプに対して異なる睡眠時間を設定できます。

- `--skip-unavailable-fragments`<br>
  DASH、hlsnative、ISMダウンロードで利用できないフラグメントをスキップします（デフォルト）。
  （エイリアス：`--no-abort-on-unavailable-fragments`）

- `--abort-on-unavailable-fragments`<br>
  フラグメントが利用できない場合、ダウンロードを中止します。
  （エイリアス：`--no-skip-unavailable-fragments`）

- `--keep-fragments`<br>
  ダウンロードが完了した後、ダウンロードしたフラグメントをディスクに保持します。

- `--no-keep-fragments`<br>
  ダウンロードが完了した後、ダウンロードしたフラグメントを削除します（デフォルト）。

- `--buffer-size SIZE`<br>
  ダウンロードバッファのサイズ。例：1024または16K（デフォルトは1024）。

- `--resize-buffer`<br>
  バッファサイズが自動的に調整されます（デフォルトの`--buffer-size`から開始）。

- `--no-resize-buffer`<br>
  バッファサイズを自動的に調整しません。

- `--http-chunk-size SIZE`<br>
  チャンクベースのHTTPダウンロードのチャンクサイズ。例：10485760または10M（デフォルトは無効）。
  ウェブサーバーによる帯域制限を回避するために役立つ場合があります（実験的）。

- `--playlist-random`<br>
  プレイリストの動画をランダムな順序でダウンロードします。

- `--lazy-playlist`<br>
  プレイリストのエントリを受信する際に処理します。これにより`n_entries`、`--playlist-random`、`--playlist-reverse`が無効になります。

- `--no-lazy-playlist`<br>
  プレイリストのすべての動画を解析した後にのみ処理します（デフォルト）。

- `--xattr-set-filesize`<br>
  ファイルのx属性`ytdl.filesize`に予想されるファイルサイズを設定します。

- `--hls-use-mpegts`<br>
  HLSビデオ用にmpegtsコンテナを使用します。これにより、いくつかのプレーヤーでビデオをダウンロード中に再生できるようになり、ダウンロードが中断された場合のファイル破損のリスクが減少します。
  これはライブストリームのダウンロード時にデフォルトで有効です。

- `--no-hls-use-mpegts`<br>
  HLSビデオでmpegtsコンテナを使用しません。ライブストリーム以外のダウンロード時はこれがデフォルトです。

- `--download-sections REGEX`<br>
  正規表現に一致するチャプターのみをダウンロードします。
  `*`プレフィックスを使うと、チャプターではなく時間範囲を指定できます。負のタイムスタンプは終了から計算されます。
  `*from-url`を使うと、URLから抽出した`start_time`と`end_time`の間をダウンロードできます。
  このオプションは複数回使用して複数のセクションをダウンロードできます。例：`--download-sections "*10:15-inf"`、`--download-sections "intro"`。

- `--downloader [PROTO:]NAME`<br>
  使用する外部ダウンローダーの名前またはパス。プロトコル（http、ftp、m3u8、dash、rstp、rtmp、mms）を指定して、それに対応するダウンローダーを指定できます。
  現在サポートされているダウンローダー：`native`、`aria2c`、`avconv`、`axel`、`curl`、`ffmpeg`、`httpie`、`wget`。
  このオプションは、異なるプロトコルに対して異なるダウンローダーを設定するために複数回使用できます。例：`--downloader aria2c --downloader "dash,m3u8:native"`は、http/ftpダウンロードにaria2cを、dash/m3u8ダウンロードにnativeダウンローダーを使用します。
  （エイリアス：`--external-downloader`）

- `--downloader-args NAME:ARGS`<br>
  外部ダウンローダーに渡す引数を指定します。ダウンローダー名と引数をコロン`:`で区切って指定します。
  `ffmpeg`には、`--postprocessor-args`と同じ構文を使って異なる位置に引数を渡すことができます。
  このオプションは、異なるダウンローダーに異なる引数を渡すために複数回使用できます。
  （エイリアス：`--external-downloader-args`）




### Filesystem Options

- `-a, --batch-file FILE`<br>
  ダウンロードするURLを含むファイル（"-"で標準入力）。各行に1つのURLを記載します。`#`、`;`、または`]`で始まる行はコメントとして扱われ、無視されます。

- `--no-batch-file`<br>
  バッチファイルからURLを読み込まない（デフォルト）。

- `-P, --paths [TYPES:]PATH`<br>
  ファイルをダウンロードするパスを指定します。ファイルの種類とパスをコロン（`:`）で区切って指定します。`--output`と同じTYPESがサポートされます。さらに、「home」（デフォルト）や「temp」パスを指定することもできます。すべての中間ファイルはまずtempパスにダウンロードされ、ダウンロードが完了した後に最終ファイルがhomeパスに移動されます。このオプションは、`--output`が絶対パスの場合は無視されます。

- `-o, --output [TYPES:]TEMPLATE`<br>
  出力ファイル名のテンプレート。詳細は「OUTPUT TEMPLATE」を参照してください。

- `--output-na-placeholder TEXT`<br>
  `--output`に指定されたフィールドが利用できない場合のプレースホルダ（デフォルトは"NA"）。

- `--restrict-filenames`<br>
  ファイル名をASCII文字のみに制限し、`&`やスペースをファイル名に含めないようにします。

- `--no-restrict-filenames`<br>
  ファイル名にUnicode文字、`&`、スペースを許可します（デフォルト）。

- `--windows-filenames`<br>
  ファイル名をWindows互換に強制します。

- `--no-windows-filenames`<br>
  ファイル名を最小限にサニタイズします。

- `--trim-filenames LENGTH`<br>
  ファイル名の長さ（拡張子を除く）を指定した文字数に制限します。

- `-w, --no-overwrites`<br>
  既存のファイルを上書きしません。

- `--force-overwrites`<br>
  すべてのビデオとメタデータファイルを上書きします。このオプションには`--no-continue`も含まれます。

- `--no-force-overwrites`<br>
  ビデオは上書きせず、関連するファイルのみを上書きします（デフォルト）。

- `-c, --continue`<br>
  部分的にダウンロードされたファイルやフラグメントを再開します（デフォルト）。

- `--no-continue`<br>
  部分的にダウンロードされたフラグメントを再開しません。ファイルがフラグメントでない場合、ダウンロードは最初からやり直されます。

- `--part`<br>
  `.part`ファイルを使用して、出力ファイルに直接書き込まずにダウンロードします（デフォルト）。

- `--no-part`<br>
  `.part`ファイルを使用せず、出力ファイルに直接書き込みます。

- `--mtime`<br>
  Last-modifiedヘッダーを使用してファイルの変更時刻を設定します（デフォルト）。

- `--no-mtime`<br>
  Last-modifiedヘッダーを使用してファイルの変更時刻を設定しません。

- `--write-description`<br>
  ビデオの説明を`.description`ファイルに書き込みます。

- `--no-write-description`<br>
  ビデオの説明を書き込みません（デフォルト）。

- `--write-info-json`<br>
  ビデオのメタデータを`.info.json`ファイルに書き込みます（これには個人情報が含まれる場合があります）。

- `--no-write-info-json`<br>
  ビデオのメタデータを書き込みません（デフォルト）。

- `--write-playlist-metafiles`<br>
  `--write-info-json`や`--write-description`などを使用する際に、ビデオメタデータに加えてプレイリストメタデータも書き込みます（デフォルト）。

- `--no-write-playlist-metafiles`<br>
  `--write-info-json`や`--write-description`などを使用する際に、プレイリストメタデータを書き込みません。

- `--clean-info-json`<br>
  `infojson`からファイル名などの内部メタデータを削除します（デフォルト）。

- `--no-clean-info-json`<br>
  `infojson`にすべてのフィールドを記録します。

- `--write-comments`<br>
  ビデオのコメントを取得し、`infojson`に書き込みます。このオプションがなくても、抽出が早い場合はコメントが取得されます。
  （エイリアス：`--get-comments`）

- `--no-write-comments`<br>
  抽出が早い場合を除き、ビデオのコメントは取得しません。
  （エイリアス：`--no-get-comments`）

- `--load-info-json FILE`<br>
  ビデオ情報を含むJSONファイル（`--write-info-json`オプションで作成）を読み込みます。

- `--cookies FILE`<br>
  クッキーを読み込むためのNetscape形式のファイル。クッキージャーにダンプも可能です。

- `--no-cookies`<br>
  ファイルからクッキーを読み込んだりダンプしたりしません（デフォルト）。

- `--cookies-from-browser BROWSER[+KEYRING][:PROFILE][::CONTAINER]`<br>
  クッキーを読み込むためのブラウザ名。サポートされているブラウザは、brave、chrome、chromium、edge、firefox、opera、safari、vivaldi、whaleです。オプションで、ChromiumクッキーをLinuxで復号化するためのKEYRING、クッキーを読み込むPROFILE名/パス、Firefoxの場合はCONTAINER名を指定できます（デフォルトでは最新アクセスされたプロフィールのすべてのコンテナを使用）。

- `--no-cookies-from-browser`<br>
  ブラウザからクッキーを読み込まない（デフォルト）。

- `--cache-dir DIR`<br>
  yt-dlpがダウンロードした情報（クライアントIDや署名など）を永続的に保存するファイルシステム上の場所。デフォルトは`${XDG_CACHE_HOME}/yt-dlp`です。

- `--no-cache-dir`<br>
  ファイルシステムキャッシュを無効にします。

- `--rm-cache-dir`<br>
  すべてのファイルシステムキャッシュファイルを削除します。



### Thumbnail Options

- `--write-thumbnail`<br>
  サムネイル画像をディスクに書き込みます。

- `--no-write-thumbnail`<br>
  サムネイル画像をディスクに書き込まない（デフォルト）。

- `--write-all-thumbnails`<br>
  すべてのサムネイル画像フォーマットをディスクに書き込みます。

- `--list-thumbnails`<br>
  各ビデオの利用可能なサムネイルをリスト表示します。
  `--no-simulate` オプションを使用しない場合、シミュレートされます。



### Internet Shortcut Options

- `--write-link`<br>
  現在のプラットフォームに応じたインターネットショートカットファイルを作成します（.url, .webloc, または .desktop）。URLはOSによってキャッシュされる場合があります。

- `--write-url-link`<br>
  .url形式のWindowsインターネットショートカットを作成します。OSはファイルパスに基づいてURLをキャッシュします。

- `--write-webloc-link`<br>
  .webloc形式のmacOSインターネットショートカットを作成します。

- `--write-desktop-link`<br>
  .desktop形式のLinuxインターネットショートカットを作成します。



### Verbosity and Simulation Options

- `-q, --quiet`<br>
  クワイエットモードを有効にします。`--verbose`オプションと併用した場合、ログは標準エラー出力に表示されます。

- `--no-quiet`<br>
  クワイエットモードを無効にします（デフォルト）。

- `--no-warnings`<br>
  警告を無視します。

- `-s, --simulate`<br>
  動画をダウンロードせず、ディスクに何も書き込まないシミュレーションモードを有効にします。

- `--no-simulate`<br>
  動画をダウンロードし、オプションの表示やリストが使用されても実際にダウンロードを行います。

- `--ignore-no-formats-error`<br>
  "No video formats" エラーを無視します。実際にダウンロード可能な動画がない場合でも、メタデータの抽出ができます（実験的機能）。

- `--no-ignore-no-formats-error`<br>
  ダウンロード可能な動画フォーマットが見つからない場合、エラーを発生させます（デフォルト）。

- `--skip-download`<br>
  動画をダウンロードせず、関連するファイルだけを書き込みます（別名: `--no-download`）。

### 出力に関する設定

- `-O, --print [WHEN:]TEMPLATE`<br>
  指定したフィールド名または出力テンプレートを画面に表示します。`WHEN`をオプションとして指定し、いつ表示するかを設定できます。デフォルトは「video」です。複数回使用できます。

- `--print-to-file [WHEN:]TEMPLATE FILE`<br>
  指定したテンプレートをファイルに追加します。`WHEN` と `TEMPLATE` の値は `--print` と同じです。ファイルのパスは出力テンプレートと同じ構文を使用します。複数回使用できます。

- `-j, --dump-json`<br>
  クワイエットモードで実行し、各動画のJSON情報を表示します。`--no-simulate`が使用されない限りシミュレートモードで動作します。

- `-J, --dump-single-json`<br>
  クワイエットモードで実行し、各URLまたは`infojson`のJSON情報を表示します。シミュレートモードで動作します。URLがプレイリストを指す場合、プレイリストの全情報が一行で出力されます。

- `--force-write-archive`<br>
  エラーが発生しない限り、ダウンロードアーカイブのエントリを強制的に書き込みます。シミュレーションオプション（`-s`など）を使用してもアーカイブへの書き込みが行われます（別名: `--force-download-archive`）。

- `--newline`<br>
  進行状況バーを新しい行で表示します。

- `--no-progress`<br>
  進行状況バーを表示しません。

- `--progress`<br>
  クワイエットモードでも進行状況バーを表示します。

- `--console-title`<br>
  コンソールのタイトルバーに進行状況を表示します。

- `--progress-template [TYPES:]TEMPLATE`<br>
  進行状況の出力テンプレートを指定します。オプションで `download:`（デフォルト）、`download-title:`（コンソールタイトル）、`postprocess:` または `postprocess-title:`を指定できます。

- `--progress-delta SECONDS`<br>
  進行状況の出力間隔を秒単位で設定します（デフォルトは 0）。

- `-v, --verbose`<br>
  各種デバッグ情報を表示します。

- `--dump-pages`<br>
  ダウンロードしたページをbase64エンコードして表示し、問題をデバッグします（非常に詳細な表示）。

- `--write-pages`<br>
  ダウンロードした中間ページを現在のディレクトリにファイルとして書き込み、問題をデバッグします。

- `--print-traffic`<br>
  送信および受信したHTTPトラフィックを表示します。
