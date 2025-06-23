---
layout: default
---

<!-- =================================================================== -->
<!-- 이 부분은 사이트 디자인(CSS)입니다. 수정하지 않아도 됩니다. -->
<!-- =================================================================== -->
<style>
  body { font-family: sans-serif; line-height: 1.6; }
  table { width: 100%; border-collapse: collapse; margin-bottom: 20px; }
  th, td { border: 1px solid #ddd; padding: 8px; text-align: left; }
  th { background-color: #f2f2f2; }
  details { border: 1px solid #ddd; border-radius: 4px; margin-bottom: 10px; }
  summary { font-weight: bold; padding: 10px; cursor: pointer; background-color: #f9f9f9; }

  /* 스포일러 텍스트 스타일 */
  .spoiler-text {
    background-color: #222;
    color: transparent;
    border-radius: 4px;
    padding: 0 4px;
    cursor: pointer;
    user-select: none;
    transition: all 0.2s;
  }
  .spoiler-text:hover { background-color: #444; }
  .spoiler-text.revealed {
    background-color: transparent;
    color: inherit;
    cursor: default;
  }
</style>

<!-- =================================================================== -->
<!-- 이 부분부터 실제 사이트 내용입니다. -->
<!-- =================================================================== -->

## 🎮 게임 번역 프로젝트

이 사이트는 게임의 텍스트 번역을 제공합니다. 스포일러를 방지하기 위해 번역문은 기본적으로 가려져 있습니다.

<p>
  <button id="show-all-spoilers">모든 번역 보기</button>
  <button id="hide-all-spoilers">모든 번역 숨기기</button>
</p>

<!-- 챕터 1: <details> 태그로 챕터 전체를 숨김 -->
<details>
  <summary><strong>챕터 1: 모든 것의 시작 (클릭하여 펼치기)</strong></summary>

  <table>
    <thead>
      <tr>
        <th style="width:15%;">화자</th>
        <th style="width:42.5%;">원문 (English)</th>
        <th style="width:42.5%;">번역 (Korean) - 클릭하여 보기</th>
      </tr>
    </thead>
    <tbody>
      <!-- Jekyll(Liquid) 반복문: _data/chapter1.yml 파일의 모든 데이터를 가져와 표로 만듦 -->
      {% for line in site.data.chapter1 %}
        <tr>
          <td>{{ line.speaker }}</td>
          <td>{{ line.original }}</td>
          <td><span class="spoiler-text">{{ line.translated }}</span></td>
        </tr>
      {% endfor %}
    </tbody>
  </table>

</details>

<!-- 여기에 챕터 2를 추가하고 싶다면, 위 <details>...</details> 블록을 복사하고
     `site.data.chapter1` 부분을 `site.data.chapter2`로 바꾸면 됩니다.
     물론 `_data/chapter2.yml` 파일도 만들어야 합니다. -->


<!-- =================================================================== -->
<!-- 이 부분은 스포일러 기능을 작동시키는 JavaScript입니다. 수정하지 않아도 됩니다. -->
<!-- =================================================================== -->
<script>
  document.addEventListener('DOMContentLoaded', function() {
    const allSpoilers = document.querySelectorAll('.spoiler-text');

    allSpoilers.forEach(spoiler => {
      spoiler.addEventListener('click', () => {
        spoiler.classList.toggle('revealed');
      });
    });

    document.getElementById('show-all-spoilers').addEventListener('click', () => {
      allSpoilers.forEach(spoiler => {
        spoiler.classList.add('revealed');
      });
    });

    document.getElementById('hide-all-spoilers').addEventListener('click', () => {
      allSpoilers.forEach(spoiler => {
        spoiler.classList.remove('revealed');
      });
    });
  });
</script>
