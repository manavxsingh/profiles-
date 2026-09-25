import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class GitHubProfileGenerator {

    // Configurable User Details
    private static final String USERNAME = "your-github-username";
    private static final String FULL_NAME = "Your Name";
    private static final String VERCEL_APP_URL = "your-instance.vercel.app";
    private static final String LINKEDIN_ID = "YOUR-ID";
    private static final String INSTAGRAM_HANDLE = "YOUR-HANDLE";
    private static final String EMAIL = "YOU@EMAIL.COM";

    public static void main(String[] args) {
        String readmeContent = generateReadmeMarkdown();

        // Save generated output directly to README.md
        File file = new File("README.md");
        try (FileWriter writer = new FileWriter(file)) {
            writer.write(readmeContent);
            System.out.println("Successfully generated README.md at " + file.getAbsolutePath());
        } catch (IOException e) {
            System.err.println("Error writing README file: " + e.getMessage());
        }
    }

    public static String generateReadmeMarkdown() {
        StringBuilder sb = new StringBuilder();

        // Phase 1 — Banner with Theme Switcher
        sb.append("<picture>\n")
          .append("  <source media=\"(prefers-color-scheme: dark)\" srcset=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/main/dark.svg\">\n")
          .append("  <source media=\"(prefers-color-scheme: light)\" srcset=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/main/light.svg\">\n")
          .append("  <img alt=\"").append(FULL_NAME).append("\" src=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/main/light.svg\">\n")
          .append("</picture>\n\n");

        // Phase 2 — Stats & Streak Cards
        sb.append("<div align=\"center\">\n")
          .append("  <img width=\"100%\" src=\"https://streak-stats.demolab.com/?user=")
          .append(USERNAME).append("&hide_border=true&background=0A101F&stroke=22D3EE&ring=A78BFA&fire=10B981&currStreakLabel=22D3EE&sideLabels=94A3B8&currStreakNum=FBFAFC&sideNums=FBFAFC&dates=64748B&titleColor=22D3EE&card_width=1180\" alt=\"streak\" />\n")
          .append("  <br/>\n")
          .append("  <img width=\"49%\" src=\"https://").append(VERCEL_APP_URL).append("/api?username=")
          .append(USERNAME).append("&show_icons=true&count_private=true&include_all_commits=true&hide_rank=true&hide_border=true&title_color=22D3EE&icon_color=A78BFA&text_color=94A3B8&bg_color=0A101F&card_width=500\" alt=\"stats\" />\n")
          .append("  <img width=\"49%\" src=\"https://").append(VERCEL_APP_URL).append("/api/top-langs/?username=")
          .append(USERNAME).append("&layout=compact&langs_count=8&hide_border=true&title_color=22D3EE&text_color=94A3B8&bg_color=0A101F&card_width=500\" alt=\"top langs\" />\n")
          .append("</div>\n\n");

        // Phase 3 — Contribution Snake
        sb.append("<div align=\"center\">\n")
          .append("  <picture>\n")
          .append("    <source media=\"(prefers-color-scheme: dark)\" srcset=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/output/github-snake-dark.svg\" />\n")
          .append("    <source media=\"(prefers-color-scheme: light)\" srcset=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/output/github-snake.svg\" />\n")
          .append("    <img alt=\"Snake eating my contributions\" src=\"https://raw.githubusercontent.com/")
          .append(USERNAME).append("/").append(USERNAME).append("/output/github-snake.svg\" />\n")
          .append("  </picture>\n")
          .append("</div>\n\n");

        // Phase 4 — Social Badges
        sb.append("<div align=\"center\">\n")
          .append("  <a href=\"https://www.linkedin.com/in/").append(LINKEDIN_ID).append("/\">\n")
          .append("    <img src=\"https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white\" alt=\"LinkedIn\" />\n")
          .append("  </a>\n  &nbsp;&nbsp;\n")
          .append("  <a href=\"https://www.instagram.com/").append(INSTAGRAM_HANDLE).append("/\">\n")
          .append("    <img src=\"https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white\" alt=\"Instagram\" />\n")
          .append("  </a>\n  &nbsp;&nbsp;\n")
          .append("  <a href=\"mailto:").append(EMAIL).append("\">\n")
          .append("    <img src=\"https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white\" alt=\"Email\" />\n")
          .append("  </a>\n")
          .append("</div>\n");

        return sb.toString();
    }
}
