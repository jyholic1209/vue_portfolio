<template>
  <div class="d-gird gap-3 d-md-flex justify-content-md-center">
    <div class="card">
      <video
        ref="previewPlayer"
        class="border-bottom"
        autoplay
        muted
        id="preview"
      ></video>

      <div class="card-body">
        <h5 class="card-title">Preview</h5>
        <p class="card-text">
          Webcam <span class="badge text-bg-info">live</span>Streaming Preview
        </p>
        <div class="d-gird gap-3 d-md-flex justify-content-md-center">
          <button
            v-on:click="videoStart"
            type="button"
            class="btn btn-primary"
            id="record-button"
          >
            녹화시작
          </button>
          <button
            v-on:click="stopRecording"
            type="button"
            class="btn btn-primary"
            id="stop-button"
          >
            녹화중지
          </button>
        </div>
      </div>
    </div>
    <div class="containers">
      <div class="card">
        <video
          ref="recordingPlayer"
          class="border-bottom"
          id="recording"
        ></video>

        <div class="card-body">
          <h5 class="card-title">Recording</h5>
          <p class="card-text">
            Webcam <span class="badge text-bg-danger">record</span> Streaming
            Playing
          </p>
          <div class="d-gird gap-3 d-md-flex justify-content-md-center">
            <button
              v-on:click="playRecording"
              type="button"
              class="btn btn-success"
              id="play-button"
            >
              녹화보기
            </button>
            <a
              ref="downButton"
              href=""
              type="button"
              class="btn btn-success"
              id="down-button"
              >다운로드</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Webcam-page",
  data() {
    return {
      recorder: null,
      recordedChunks: [],
      stream: null,
      recordingUrl: null,
    };
  },
  methods: {
    videoStart() {
      this.$refs.previewPlayer.srcObject = null;
      this.recordedChunks = [];

      navigator.mediaDevices
        .getUserMedia({ audio: true, video: true })
        .then((mediaStream) => {
          this.stream = mediaStream;
          this.recorder = new MediaRecorder(mediaStream, {
            audio: true,
            video: true,
          });

          this.$refs.previewPlayer.srcObject = mediaStream;

          this.recorder.ondataavailable = (e) => {
            this.recordedChunks.push(e.data);
          };
          this.recorder.start();
        })
        .catch((err) => {
          console.log(`${err.name} : ${err.message}`);
        });
    },
    stopRecording() {
      this.stream.getTracks().forEach((e) => {
        e.stop();
      });
      this.recorder.stop();
      this.recorder.onerror = (e) => {
        throw e.error || new Error(e.name);
      };
    },
    playRecording() {
      const recordedBlob = new Blob(this.recordedChunks, {
        type: "video/webm",
      });

      this.$refs.recordingPlayer.src = URL.createObjectURL(recordedBlob);
      this.recordingUrl = this.$refs.recordingPlayer.src;

      this.$refs.recordingPlayer.play();
      this.$refs.recordingPlayer.onerror = (e) => {
        throw e.error || new Error(e.name);
      };
      this.$refs.downButton.href = this.recordingUrl;
      this.$refs.downButton.download = `recorded_${new Date()}.webm`;
    },
  },
};
</script>

<style scoped>
video {
  width: 360px;
  height: 270px;
}
</style>
