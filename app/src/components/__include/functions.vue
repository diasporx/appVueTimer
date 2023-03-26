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
            stopwatch.status = 'paused';
            setInterval(() => {
                stopwatch.time = 0;
            }, 1)
        },
        addStopwatch() {
            this.stopwatches.push({
                id: this.nextId,
                time: 0,
                status: 'paused'
            });
            this.nextId++;
        },
        formatTime(time) {
            const seconds = Math.floor(time / 1000) % 60;
            const minutes = Math.floor(time / (1000 * 60)) % 60;
            const hours = Math.floor(time / (1000 * 60 * 60));

            let formattedTime = `${seconds < 10 ? '0' : ''}${seconds}`;

            if (hours > 0) {
                formattedTime = `${minutes < 10 ? '0' : ''}${minutes}:${formattedTime}`;
                formattedTime = `${hours}:${formattedTime}`;
            } else if (minutes > 0) {
                formattedTime = `${minutes}:${formattedTime}`;
            }

            return formattedTime;
        }

    }

}
</script>