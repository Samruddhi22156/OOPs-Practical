import java.awt.*;
import javax.swing.*;

public class TransformTriangleAll extends JPanel {
    double angle; // rotation angle in radians
    double scaleX, scaleY;
    int tx, ty; // translation values
    double shx, shy; // shear factors

    public TransformTriangleAll() {
        this.angle = Math.toRadians(45); // rotate 45 degrees
        this.scaleX = 1.5; // scale 1.5x in X
        this.scaleY = 1.2; // scale 1.2x in Y
        this.tx = 100; // translate +100 in X
        this.ty = 50; // translate +50 in Y
        this.shx = 0.5; // shear factor in X
        this.shy = 0.3; // shear factor in Y
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2 = (Graphics2D) g;

        // Define triangle in positive coordinates
        int[] xPoints = { 100, 150, 200 };
        int[] yPoints = { 200, 100, 200 };

        // === Original (Blue) ===
        g2.setColor(Color.BLUE);
        g2.drawPolygon(xPoints, yPoints, 3);

        // === Translation (Green) ===
        int[] xTranslated = new int[3];
        int[] yTranslated = new int[3];
        for (int i = 0; i < 3; i++) {
            xTranslated[i] = xPoints[i] + tx;
            yTranslated[i] = yPoints[i] + ty;
        }
        g2.setColor(Color.GREEN);
        g2.drawPolygon(xTranslated, yTranslated, 3);

        // === Scaling (Orange) ===
        int[] xScaled = new int[3];
        int[] yScaled = new int[3];
        for (int i = 0; i < 3; i++) {
            xScaled[i] = (int) (xPoints[i] * scaleX);
            yScaled[i] = (int) (yPoints[i] * scaleY);
        }
        g2.setColor(Color.ORANGE);
        g2.drawPolygon(xScaled, yScaled, 3);

        // === Rotation around center (Red) ===
        int[] xRotated = new int[3];
        int[] yRotated = new int[3];

        // Step 1: Find center of triangle
        double cx = (xPoints[0] + xPoints[1] + xPoints[2]) / 3.0;
        double cy = (yPoints[0] + yPoints[1] + yPoints[2]) / 3.0;

        for (int i = 0; i < 3; i++) {
            // Step 2: Shift to origin
            double xShifted = xPoints[i] - cx;
            double yShifted = yPoints[i] - cy;

            // Step 3: Rotate
            double xRot = xShifted * Math.cos(angle) - yShifted * Math.sin(angle);
            double yRot = xShifted * Math.sin(angle) + yShifted * Math.cos(angle);

            // Step 4: Shift back
            xRotated[i] = (int) (xRot + cx);
            yRotated[i] = (int) (yRot + cy);
        }

        g2.setColor(Color.RED);
        g2.drawPolygon(xRotated, yRotated, 3);

        // === Shear (Purple) ===
        int[] xShear = new int[3];
        int[] yShear = new int[3];
        for (int i = 0; i < 3; i++) {
            xShear[i] = (int) (xPoints[i] + shx * yPoints[i]);
            yShear[i] = (int) (yPoints[i] + shy * xPoints[i]);
        }
        g2.setColor(Color.MAGENTA);
        g2.drawPolygon(xShear, yShear, 3);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("2D Transformations - Triangle (All)");
        TransformTriangleAll panel = new TransformTriangleAll();

        frame.add(panel);
        frame.setSize(700, 700);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
