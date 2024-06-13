<template>
    <div class="ItemList">
        <div class="content">
            <iframe width="300" height="190" src="https://www.youtube.com/embed/jdTsJzXmgU0?si=fOC2f7_3qiSgFj24" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>자바 수업을 리뉴얼 했습니다</p>
        </div>
        <div class="content">
            <iframe width="300" height="190" src="https://www.youtube.com/embed/qR90tdW0Hbo?si=-pYicpLqVfnLPVuB" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>Java - 소개와 수업 소개</p>
        </div>
        <div class="content">
            <iframe width="300" height="190" src="https://www.youtube.com/embed/kyFrm3zKryE?si=O0pX4HuFpd4EccBf" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>Java - 설치</p>
        </div>
        <div class="content">
            <iframe width="300" height="190" src="https://www.youtube.com/embed/2HNmQaMQiw4?si=FSYTQ5MmY45ps182" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>Java - 설치와 실행2 : 리눅스에 Java ...</p>
        </div>
        <div class="content">
            <iframe width="300" height="190" src="https://www.youtube.com/embed/mBIgiAl9trI?si=fSBrd4oCA8FZZQDT" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>Java - 설치와 실행2 : 리눅스에 Java ...</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'TestList'
}
</script>

<style>
    .player {
        margin-right: 10px;
    }
    .ItemList {
        overflow-x: auto;
        white-space: nowrap;
        display: flex;
    }
    .content {
        text-align: left;
        font-size: 17px;
        font-weight: bold;
    }
</style>
