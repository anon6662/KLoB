# KLoB
Data for KLoB: a Benchmark for Assessing Knowledge Locating Methods in Language Models.

## Examples
### KLoB-c
  {"prompts": ["The native language of Norman Rockwell is _", "The mother tongue of Norman Rockwell is _", "The language Norman Rockwell speaks at hometown is _"], "knowledge": ["Norman Rockwell", "native_(P103)", "English"]}

### KLoB-r
  {"single_knowledge": ["Ann Druyan", "spouse_(P26)", "Carl Sagan"], "knowledge_chain": ["Ann Druyan", "spouse_(P26)", "Carl Sagan", "employer_(P108)", "Cornell University"], "single_knowlege_prompts": ["Ann Druyan is married to _", "The spouse of Ann Druyan is none other than _", "In matrimony, Ann Druyan is bound to _"], "knowlege_chain_prompt": "the employer of the spouse of Ann Druyan is _"}

### KLoB-u
  "extirpation sensa subiodide conquedle spikebill drabbish unvalidating becuiba _"


处理前：
<div style="background-color: #f0f0f0; padding: 10px; border: 1px solid #ccc; font-style: italic;">

<span style="background-color: #ffff99;">*First published in 2015*</span>


<span style="background-color: #ffff99;">*Allen & Unwin*</span>

<span style="background-color: #ffff99;">*83 Alexander Street*</span>

<span style="background-color: #ffff99;">*Crows Nest NSW 2065*</span>

<span style="background-color: #ffff99;">*Australia*</span>

<span style="background-color: #ffff99;">*Phone: (61 2) 8425 0100*</span>

<span style="background-color: #ffff99;">*Cataloguing-in-Publication details are available from the National Library of Australia*</span>

<span style="background-color: #ffff99;">*ISBN 978 1 74331 9208*</span>

<span style="background-color: #ffff99;">*eISBN 978 1 74343 637 0*</span>

<span style="background-color: #ffff99;">*Internal design by Christabella Designs*</span>

<span style="background-color: #ffff99;">*Typeset by Post Pre-press Group, Australia*</span>

<span style="background-color: #ffff99;">*Extracts from The Kite Runner by Khaled Hosseini © Bloomsbury Publishing UK*</span>


<span style="background-color: #ffff99;">*CONTENTS*</span>

<span style="background-color: #ffff99;">*ZARA*</span>

<span style="background-color: #ffff99;">*LILI*</span>

<span style="background-color: #ffff99;">*EVE*</span>

<span style="background-color: #ffff99;">...</span>


*Zara*

*She was standing at the end of the hall in the late afternoon light, her back arched against the wall, between two landscape paintings. Closing her eyes, she ran her hands up and down the red dress clinging to her curves. The dress had been designed by a genius. Its neckline was low enough to be provocative, but the hemline was below knee-length—too long for Leo, the husband of our hostess, to …*
</div>


处理后：
<div style="background-color: #f0f0f0; padding: 10px; border: 1px solid #ccc; font-style: italic;">


*Zara*

*She was standing at the end of the hall in the late afternoon light, her back arched against the wall, between two landscape paintings. Closing her eyes, she ran her hands up and down the red dress clinging to her curves. The dress had been designed by a genius. Its neckline was low enough to be provocative, but the hemline was below knee-length—too long for Leo, the husband of our hostess, to …*
</div>
