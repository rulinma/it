# EventSource

* JavaScript 代码

    ```javascript
       useEffect(() => {
        const eventSource = new EventSource('http://localhost:5005/api/sse/' + uid);
        eventSource.onmessage = (event) => {
            console.log(event.data);
        };
        return () => {
            eventSource.close();
        };
    }, []);
    ```

    ```javascript
    const eventSource = new EventSource('http://localhost:5005/api/sse/' + uid);

    eventSource.onmessage = (event) => {
        // console.log(event);
        console.log(event.data);
    };
    eventSource.close = () => {
        eventSource.close();
    };
    ```

* Flask 代码

    ```python
    @app.route('/api/sse/<uuid>', methods=['GET', 'POST'])
    def sse(uuid):
        logging.info(uuid)
    ```

* Java 代码

    ```java
    @RequestMapping(value = "/sse/{uid}", method = {RequestMethod.POST, RequestMethod.GET})
    public SseEmitter getSse(@PathVariable String uid, HttpServletRequest request, HttpServletResponse response) {
        log.info("uid {} , request {}", uid, request);
        response.setContentType("text/event-stream");
        SseEmitter emitter = new SseEmitter(5000L);
        emitter.onCompletion(() -> log.info("SSE流关闭"));
        emitter.onError((e) -> log.error("SSE发生错误", e));

        ExecutorService sseMvcExecutor = Executors.newSingleThreadExecutor();
        sseMvcExecutor.execute(() -> {
            try {
                for (int i = 0; true; i++) {
                    SseEmitter.SseEventBuilder event = SseEmitter.event()
                            .data("data: SSE MVC - " + LocalTime.now().toString() + "\n\n")
                            .id(String.valueOf(i))
                            .name("sse event - mvc");
                    emitter.send(event);
                    Thread.sleep(5000);
                }
            } catch (Exception ex) {
                emitter.completeWithError(ex);
            }
        });

        return emitter;
    }
    ```
