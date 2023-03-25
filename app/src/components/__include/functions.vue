<script>
export default {
    methods: {
        startStopwatch(stopwatch) {
            stopwatch.status = 'running';
            const startTime = Date.now() - stopwatch.time;
            const updateTimer = () => {
                stopwatch.time = Date.now() - startTime;
                if (stopwatch.status === 'running') {
                    requestAnimationFrame(updateTimer);
                }
            };
            requestAnimationFrame(updateTimer);
        },
        pauseStopwatch(stopwatch) {
            stopwatch.status = 'paused';
        },
        resetStopwatch(stopwatch) {
            stopwatch.time = 0;
            stopwatch.status = 'paused';
        },
        addStopwatch() {
            this.stopwatches.push({ time: 0, status: 'paused' });
        },
        formatTime(time) {
            const seconds = Math.floor(time / 1000) % 60;
            const minutes = Math.floor(time / (1000 * 60)) % 60;
            const hours = Math.floor(time / (1000 * 60 * 60));

            let formattedTime = `${seconds}`;

            if (minutes > 0) {
                formattedTime = `${minutes}:${formattedTime}`;
            }

            if (hours > 0) {
                formattedTime = `${hours}:${formattedTime}`;
            }

            return formattedTime;
        },

    }

}
</script>