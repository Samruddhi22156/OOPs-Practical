// TwoUserDemo.java
// Program based on your handwritten version

class ChatUser extends Thread {
    private volatile boolean paused = false;
    private volatile boolean running = true;

    ChatUser(String name) {
        super(name); // Thread name
    }

    @Override
    public void run() {
        int i = 1;
        while (running && i <= 5) {
            if (!paused) {
                System.out.println(getName() + " say: Message " + i);
                i++;
                try {
                    Thread.sleep(500); // delay between messages
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        }
        System.out.println(getName() + " finished chatting");
    }

    // pause/resume/stop methods
    public void pauseChat() {
        paused = true;
    }

    public void resumeChat() {
        paused = false;
    }

    public void stopChat() {
        running = false;
    }
}

public class TwoUserDemo {
    public static void main(String[] args) throws Exception {
        ChatUser u1 = new ChatUser("Alice");
        ChatUser u2 = new ChatUser("Bob");

        // set priority
        u1.setPriority(Thread.MAX_PRIORITY);
        u2.setPriority(Thread.MIN_PRIORITY);

        // start both
        u1.start();
        u2.start();

        // check Alive
        System.out.println("Alice alive? " + u1.isAlive());

        // pause Bob for a while
        Thread.sleep(1000);
        u2.pauseChat();
        System.out.println("Bob paused...");

        Thread.sleep(1000);
        u2.resumeChat();
        System.out.println("Bob resumed...");

        // stop Alice early
        Thread.sleep(1000);
        u1.stopChat();
        System.out.println("Alice stopped...");

        // wait for both to finish
        u1.join();
        u2.join();

        System.out.println("Alice alive after join? " + u1.isAlive());
        System.out.println("Chat ended.");
    }
}
