# สคริปต์การสอน: WPF Episode 06 - DockPanel

## เนื้อหาที่จะสอน

### 1. DockPanel คืออะไร
- Panel สำหรับจัด Layout แบบ Dock ไปที่ขอบต่างๆ
- เหมาะสำหรับสร้าง Main Window Layout

### 2. DockPanel.Dock Property
- Top, Bottom, Left, Right
- LastChildFill Property

### 3. สร้าง Application Layout
- Header/Menu Bar
- Footer/Status Bar
- Sidebar
- Main Content Area

---

## ส่วนที่ 1: Introduction (0:00 - 2:00)

**สวัสดีครับทุกคน**

ยินดีต้อนรับกลับมาสู่ WPF Tutorial Series ของเรา

วันนี้เราจะมาเรียนรู้เกี่ยวกับ **DockPanel** ซึ่งเป็น Layout Panel ที่มีประโยชน์มากครับ

ถ้าเราเคยใช้โปรแกรมต่างๆ เช่น Visual Studio, Word, Photoshop 
จะเห็นว่ามันมี Menu Bar ด้านบน, Status Bar ด้านล่าง, Sidebar ข้างๆ

**DockPanel ถูกออกแบบมาเพื่อสร้าง Layout แบบนี้โดยเฉพาะครับ!**

---

## ส่วนที่ 2: DockPanel คืออะไร (2:00 - 5:00)

### Demo 2.1: DockPanel เปล่าๆ

เริ่มต้นด้วย DockPanel เปล่าๆ ก่อน

```xml
<DockPanel>
</DockPanel>
```

DockPanel จะจัด Element ให้ "Dock" หรือ "เกาะ" ไปที่ขอบต่างๆ ของ Panel

### Demo 2.2: แนวคิดของ Dock

คำว่า "Dock" แปลว่า "ท่าเรือ" หรือ "เกาะ"

เหมือนเรือที่เทียบท่า จอด "เกาะ" อยู่กับท่าเรือ

ใน DockPanel เราก็บอกว่า Element จะ "เกาะ" ที่ขอบไหน:
- **Top** (บน)
- **Bottom** (ล่าง)
- **Left** (ซ้าย)
- **Right** (ขวา)

---

## ส่วนที่ 3: DockPanel.Dock Property (5:00 - 12:00)

### Demo 3.1: Dock="Top"

ลองสร้าง Element แรกที่ Dock ด้านบน

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top" 
                   HorizontalAlignment="Center" 
                   VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**อธิบาย:**
- `DockPanel.Dock="Top"` - บอกว่า Element นี้จะเกาะด้านบน
- `Height="50"` - กำหนดความสูง 50 pixels
- Border จะยืดเต็มความกว้างของ DockPanel

### Demo 3.2: เพิ่ม Dock="Bottom"

ตอนนี้เพิ่มด้านล่าง

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Bottom" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**เห็นไหมครับ:**
- Border แรก Dock ด้านบน
- Border ที่สอง Dock ด้านล่าง
- ตรงกลางยังว่างอยู่

### Demo 3.3: เพิ่ม Dock="Left"

มาเพิ่มด้านซ้ายกัน

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Bottom" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Left" Background="LightCoral" Width="100">
        <TextBlock Text="Left" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**สังเกตไหมครับ:**
- Border ด้านซ้ายจะ Dock ระหว่าง Top และ Bottom
- มันไม่ได้เต็มความสูงทั้งหมด แต่เต็มเฉพาะช่วงที่เหลือ

### Demo 3.4: เพิ่ม Dock="Right"

เพิ่มด้านขวาด้วย

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Bottom" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Left" Background="LightCoral" Width="100">
        <TextBlock Text="Left" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
    
    <Border DockPanel.Dock="Right" Background="LightYellow" Width="100">
        <TextBlock Text="Right" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**ตอนนี้มีครบทั้ง 4 ด้านแล้ว!**
- Top (บน)
- Bottom (ล่าง)
- Left (ซ้าย)
- Right (ขวา)
- **ตรงกลางยังว่างอยู่**

---

## ส่วนที่ 4: LastChildFill Property (12:00 - 16:00)

### Demo 4.1: Element สุดท้าย

ตอนนี้เพิ่ม Element สุดท้ายเข้าไป

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top"/>
    </Border>
    
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Bottom"/>
    </Border>
    
    <Border DockPanel.Dock="Left" Background="LightCoral" Width="100">
        <TextBlock Text="Left"/>
    </Border>
    
    <Border DockPanel.Dock="Right" Background="LightYellow" Width="100">
        <TextBlock Text="Right"/>
    </Border>
    
    <!-- Element สุดท้าย ไม่ต้อง Dock -->
    <Border Background="White">
        <TextBlock Text="Center" 
                   FontSize="24" 
                   HorizontalAlignment="Center" 
                   VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**สังเกตไหมครับ:**
- Element สุดท้าย **ไม่มี DockPanel.Dock**
- มันจะเต็มพื้นที่ตรงกลางที่เหลืออัตโนมัติ
- นี่คือ **LastChildFill** ครับ (Default = true)

### Demo 4.2: LastChildFill="False"

ลองปิด LastChildFill ดู

```xml
<DockPanel LastChildFill="False">
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Top"/>
    </Border>
    
    <Border Background="White">
        <TextBlock Text="Center"/>
    </Border>
</DockPanel>
```

**เมื่อ LastChildFill="False":**
- Element สุดท้ายจะไม่เต็มพื้นที่กลาง
- มันจะใช้ขนาดตามเนื้อหา

**โดยปกติไม่ต้องตั้ง เพราะ Default เป็น True อยู่แล้วครับ**

---

## ส่วนที่ 5: ลำดับสำคัญ! (16:00 - 20:00)

### Demo 5.1: ลำดับมีผล

**สิ่งสำคัญ:** ลำดับที่เขียน Element มีผลต่อ Layout!

**ตัวอย่างที่ 1: Top → Left**

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="Red" Height="50">
        <TextBlock Text="Top First"/>
    </Border>
    
    <Border DockPanel.Dock="Left" Background="Blue" Width="100">
        <TextBlock Text="Left Second"/>
    </Border>
    
    <Border Background="White"/>
</DockPanel>
```

**ผลลัพธ์:**
- Top จะเต็มความกว้าง
- Left จะอยู่ด้านล่าง Top

**ตัวอย่างที่ 2: Left → Top**

```xml
<DockPanel>
    <Border DockPanel.Dock="Left" Background="Blue" Width="100">
        <TextBlock Text="Left First"/>
    </Border>
    
    <Border DockPanel.Dock="Top" Background="Red" Height="50">
        <TextBlock Text="Top Second"/>
    </Border>
    
    <Border Background="White"/>
</DockPanel>
```

**ผลลัพธ์:**
- Left จะเต็มความสูง
- Top จะอยู่ทางขวา Left

**ข้อสรุป:**
- Element ที่ Dock ก่อน จะได้พื้นที่เต็มก่อน
- Element ที่ Dock ทีหลัง จะได้พื้นที่ที่เหลือ

### Demo 5.2: Best Practice

**แนะนำให้เรียงตามนี้:**

1. Top
2. Bottom
3. Left
4. Right
5. Center (ไม่ต้อง Dock)

```xml
<DockPanel>
    <!-- 1. Top -->
    <Border DockPanel.Dock="Top" Height="50"/>
    
    <!-- 2. Bottom -->
    <Border DockPanel.Dock="Bottom" Height="40"/>
    
    <!-- 3. Left -->
    <Border DockPanel.Dock="Left" Width="150"/>
    
    <!-- 4. Right -->
    <Border DockPanel.Dock="Right" Width="100"/>
    
    <!-- 5. Center -->
    <Border Background="White"/>
</DockPanel>
```

---

## ส่วนที่ 6: สร้าง Application Layout จริง (20:00 - 28:00)

### Demo 6.1: Header / Menu Bar

มาสร้าง Application Layout จริงๆ กันเลย!

```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#4A90E2" Height="50">
        <TextBlock Text="Header / Menu Bar" 
                   FontSize="20" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>
</DockPanel>
```

**อธิบาย:**
- `Background="#4A90E2"` - สีน้ำเงินสวยๆ
- `FontSize="20"` - ตัวอักษรใหญ่
- `Foreground="White"` - ตัวอักษรสีขาว

### Demo 6.2: เพิ่ม Footer / Status Bar

```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#4A90E2" Height="50">
        <TextBlock Text="Header / Menu Bar" 
                   FontSize="20" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>

    <!-- Footer -->
    <Border DockPanel.Dock="Bottom" Background="#34495E" Height="40">
        <TextBlock Text="Footer / Status Bar" 
                   FontSize="14" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>
</DockPanel>
```

**อธิบาย:**
- `Background="#34495E"` - สีเทาเข้ม
- `Height="40"` - เตี้ยกว่า Header เล็กน้อย

### Demo 6.3: เพิ่ม Sidebar

```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#4A90E2" Height="50">
        <TextBlock Text="Header / Menu Bar" 
                   FontSize="20" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>

    <!-- Footer -->
    <Border DockPanel.Dock="Bottom" Background="#34495E" Height="40">
        <TextBlock Text="Footer / Status Bar" 
                   FontSize="14" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>

    <!-- Sidebar -->
    <Border DockPanel.Dock="Left" Background="#ECF0F1" Width="150">
        <StackPanel Margin="10">
            <TextBlock Text="Sidebar" FontWeight="Bold" Margin="0,0,0,10"/>
            <Button Content="Menu 1" Margin="0,5"/>
            <Button Content="Menu 2" Margin="0,5"/>
            <Button Content="Menu 3" Margin="0,5"/>
        </StackPanel>
    </Border>
</DockPanel>
```

**อธิบาย:**
- `Background="#ECF0F1"` - สีเทาอ่อน
- `Width="150"` - กว้าง 150 pixels
- ใช้ `StackPanel` ข้างในเพื่อวาง Menu

### Demo 6.4: เพิ่ม Main Content Area

```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#4A90E2" Height="50">
        <TextBlock Text="Header / Menu Bar" 
                   FontSize="20" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>

    <!-- Footer -->
    <Border DockPanel.Dock="Bottom" Background="#34495E" Height="40">
        <TextBlock Text="Footer / Status Bar" 
                   FontSize="14" 
                   Foreground="White" 
                   VerticalAlignment="Center" 
                   HorizontalAlignment="Center"/>
    </Border>

    <!-- Sidebar -->
    <Border DockPanel.Dock="Left" Background="#ECF0F1" Width="150">
        <StackPanel Margin="10">
            <TextBlock Text="Sidebar" FontWeight="Bold" Margin="0,0,0,10"/>
            <Button Content="Menu 1" Margin="0,5"/>
            <Button Content="Menu 2" Margin="0,5"/>
            <Button Content="Menu 3" Margin="0,5"/>
        </StackPanel>
    </Border>

    <!-- Main Content (LastChildFill) -->
    <Border Background="White">
        <TextBlock Text="Main Content Area" 
                   FontSize="24" 
                   HorizontalAlignment="Center" 
                   VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

**ครบแล้วครับ!**

ตอนนี้เรามี Application Layout ที่สมบูรณ์:
- ✅ Header ด้านบน
- ✅ Footer ด้านล่าง
- ✅ Sidebar ด้านซ้าย
- ✅ Main Content ตรงกลาง

---

## ส่วนที่ 7: ตัวอย่างการใช้งานจริง (28:00 - 33:00)

### 7.1 Visual Studio Style Layout

```xml
<DockPanel>
    <!-- Menu Bar -->
    <Border DockPanel.Dock="Top" Background="#2D2D30" Height="30">
        <StackPanel Orientation="Horizontal">
            <TextBlock Text="File" Foreground="White" Margin="10,0" VerticalAlignment="Center"/>
            <TextBlock Text="Edit" Foreground="White" Margin="10,0" VerticalAlignment="Center"/>
            <TextBlock Text="View" Foreground="White" Margin="10,0" VerticalAlignment="Center"/>
        </StackPanel>
    </Border>
    
    <!-- Toolbar -->
    <Border DockPanel.Dock="Top" Background="#3E3E42" Height="40">
        <StackPanel Orientation="Horizontal" Margin="5">
            <Button Content="▶" Width="30" Margin="2"/>
            <Button Content="■" Width="30" Margin="2"/>
            <Button Content="💾" Width="30" Margin="2"/>
        </StackPanel>
    </Border>
    
    <!-- Status Bar -->
    <Border DockPanel.Dock="Bottom" Background="#007ACC" Height="25">
        <TextBlock Text="Ready" Foreground="White" Margin="10,0" VerticalAlignment="Center"/>
    </Border>
    
    <!-- Solution Explorer -->
    <Border DockPanel.Dock="Right" Background="#252526" Width="200">
        <TextBlock Text="Solution Explorer" Foreground="White" Margin="10"/>
    </Border>
    
    <!-- Code Editor -->
    <Border Background="#1E1E1E">
        <TextBlock Text="Code Editor Area" Foreground="White" 
                   HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### 7.2 Browser Style Layout

```xml
<DockPanel>
    <!-- Address Bar -->
    <Border DockPanel.Dock="Top" Background="WhiteSmoke" Height="40">
        <Grid Margin="10,0">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="Auto"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="Auto"/>
            </Grid.ColumnDefinitions>
            <Button Grid.Column="0" Content="←" Width="30" Margin="2"/>
            <TextBox Grid.Column="1" Text="https://example.com" VerticalContentAlignment="Center" Margin="5,0"/>
            <Button Grid.Column="2" Content="Go" Width="50" Margin="2"/>
        </Grid>
    </Border>
    
    <!-- Status Bar -->
    <Border DockPanel.Dock="Bottom" Background="LightGray" Height="25">
        <TextBlock Text="Done" Margin="10,0" VerticalAlignment="Center"/>
    </Border>
    
    <!-- Bookmarks Sidebar -->
    <Border DockPanel.Dock="Left" Background="#F5F5F5" Width="180">
        <StackPanel Margin="10">
            <TextBlock Text="Bookmarks" FontWeight="Bold" Margin="0,0,0,10"/>
            <TextBlock Text="• Google" Margin="0,3"/>
            <TextBlock Text="• GitHub" Margin="0,3"/>
            <TextBlock Text="• StackOverflow" Margin="0,3"/>
        </StackPanel>
    </Border>
    
    <!-- Web Page Content -->
    <Border Background="White">
        <TextBlock Text="Web Page Content" 
                   HorizontalAlignment="Center" 
                   VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### 7.3 Email Client Layout

```xml
<DockPanel>
    <!-- Toolbar -->
    <Border DockPanel.Dock="Top" Background="#0078D4" Height="50">
        <StackPanel Orientation="Horizontal" Margin="10,0">
            <Button Content="New" Width="60" Margin="5"/>
            <Button Content="Reply" Width="60" Margin="5"/>
            <Button Content="Delete" Width="60" Margin="5"/>
        </StackPanel>
    </Border>
    
    <!-- Folder List (Left) -->
    <Border DockPanel.Dock="Left" Background="#F3F3F3" Width="150">
        <StackPanel Margin="10">
            <TextBlock Text="Folders" FontWeight="Bold" Margin="0,0,0,10"/>
            <TextBlock Text="📥 Inbox (5)" Margin="0,5"/>
            <TextBlock Text="📤 Sent" Margin="0,5"/>
            <TextBlock Text="🗑️ Trash" Margin="0,5"/>
        </StackPanel>
    </Border>
    
    <!-- Email List (Left after folder) -->
    <Border DockPanel.Dock="Left" Background="White" Width="250" BorderBrush="LightGray" BorderThickness="0,0,1,0">
        <StackPanel Margin="10">
            <TextBlock Text="Messages" FontWeight="Bold" Margin="0,0,0,10"/>
            <Border Background="LightBlue" Padding="10" Margin="0,5">
                <TextBlock Text="Meeting Tomorrow"/>
            </Border>
            <Border Background="White" Padding="10" Margin="0,5" BorderBrush="LightGray" BorderThickness="1">
                <TextBlock Text="Project Update"/>
            </Border>
        </StackPanel>
    </Border>
    
    <!-- Email Content -->
    <Border Background="White" Padding="20">
        <TextBlock Text="Email content will be displayed here" 
                   TextWrapping="Wrap"/>
    </Border>
</DockPanel>
```

---

## ส่วนที่ 8: DockPanel vs Grid (33:00 - 36:00)

### เมื่อไหร่ควรใช้ DockPanel vs Grid?

**ใช้ DockPanel เมื่อ:**
- สร้าง Main Window Layout (Header, Footer, Sidebar, Content)
- มี Element ที่ชัดเจนว่า Dock ไปด้านไหน
- Layout เรียบง่าย ไม่ซับซ้อนมาก
- ต้องการ Code ที่อ่านง่าย สื่อความหมาย

**ใช้ Grid เมื่อ:**
- Layout ซับซ้อน มีหลาย Row และ Column
- ต้องการ Row/Column Span
- ต้องการควบคุมขนาดแบบ Proportional (Star sizing)
- มี Element ที่ต้อง Overlap กัน

**ตัวอย่าง:**

**DockPanel ดีกว่า:**
```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>  <!-- ชัดเจนว่าอยู่ด้านบน -->
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border/>
</DockPanel>
```

**Grid ดีกว่า:**
```xml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>  <!-- Proportional -->
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
</Grid>
```

---

## ส่วนที่ 9: Tips & Best Practices (36:00 - 39:00)

### 9.1 ลำดับการ Dock

```xml
<!-- ✅ ดี: เรียงตามลำดับที่เหมาะสม -->
<DockPanel>
    <Border DockPanel.Dock="Top"/>
    <Border DockPanel.Dock="Bottom"/>
    <Border DockPanel.Dock="Left"/>
    <Border DockPanel.Dock="Right"/>
    <Border/>  <!-- Center -->
</DockPanel>

<!-- ⚠️ ใช้ได้ แต่อาจได้ Layout ไม่ตามต้องการ -->
<DockPanel>
    <Border DockPanel.Dock="Left"/>
    <Border DockPanel.Dock="Top"/>
    <Border/>
</DockPanel>
```

### 9.2 ใช้ LastChildFill

```xml
<!-- ✅ ดี: ไม่ต้องระบุ LastChildFill (Default = true) -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border/>  <!-- จะเต็มพื้นที่ที่เหลืออัตโนมัติ -->
</DockPanel>

<!-- ❌ ไม่จำเป็น: ระบุ LastChildFill="True" -->
<DockPanel LastChildFill="True">
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border/>
</DockPanel>
```

### 9.3 Nested DockPanel

สามารถซ้อน DockPanel ได้

```xml
<DockPanel>
    <!-- Outer DockPanel -->
    <Border DockPanel.Dock="Top" Height="50"/>
    
    <!-- Inner DockPanel for content area -->
    <DockPanel>
        <Border DockPanel.Dock="Left" Width="200"/>
        <Border/>
    </DockPanel>
</DockPanel>
```

### 9.4 ใช้ร่วมกับ Panel อื่น

```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50">
        <!-- ใช้ StackPanel สำหรับ Toolbar -->
        <StackPanel Orientation="Horizontal">
            <Button Content="New"/>
            <Button Content="Open"/>
            <Button Content="Save"/>
        </StackPanel>
    </Border>
    
    <Border DockPanel.Dock="Left" Width="200">
        <!-- ใช้ StackPanel สำหรับ Menu -->
        <StackPanel>
            <Button Content="Home"/>
            <Button Content="Settings"/>
        </StackPanel>
    </Border>
    
    <Border>
        <!-- ใช้ Grid สำหรับ Content Area -->
        <Grid>
            <!-- Complex layout -->
        </Grid>
    </Border>
</DockPanel>
```

---

## ส่วนที่ 10: Wrap Up และ Outro (39:00 - 42:00)

**สรุปสิ่งที่เราได้เรียนรู้วันนี้:**

1. ✅ DockPanel คือ Panel สำหรับ Dock Element ไปที่ขอบต่างๆ
2. ✅ DockPanel.Dock Property: Top, Bottom, Left, Right
3. ✅ LastChildFill Property (Default = true)
4. ✅ ลำดับการ Dock มีความสำคัญ
5. ✅ สร้าง Application Layout จริง (Header, Footer, Sidebar, Content)
6. ✅ ตัวอย่าง Real-world Applications
7. ✅ เปรียบเทียบกับ Grid

**DockPanel เหมาะสำหรับ:**
- Main Window Layout
- Application Shell
- Simple Docking Scenarios

**จุดเด่นของ DockPanel:**
- Code อ่านง่าย สื่อความหมาย
- เหมาะกับ Layout แบบ Header/Footer/Sidebar
- ไม่ซับซ้อน เข้าใจง่าย

**ในตอนต่อไป:**

เราจะมาเรียนรู้เกี่ยวกับ **Canvas** ซึ่งเป็น Panel ที่ให้เราควบคุมตำแหน่ง
แบบ Absolute Positioning (X, Y) เหมาะสำหรับทำ Drawing, Animation, Games!

**อย่าลืม:**
- กด Like ถ้าชอบ
- Subscribe เพื่อติดตามตอนต่อไป
- Comment บอกว่าอยากเรียนเรื่องอะไรต่อไป

**ขอบคุณที่รับชมครับ แล้วพบกันใหม่ตอนหน้า สวัสดีครับ!**

---

## เอกสารอ้างอิง

### Official Documentation
- [DockPanel Class - Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.dockpanel)
- [Panels Overview - Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/controls/panels-overview)

### Properties Reference
```
DockPanel.Dock: Top | Bottom | Left | Right (Attached Property)
LastChildFill: Boolean (Default = true)
Background: Color
Margin: Thickness
```

---

## Tips & Best Practices

1. **Docking Order**: Dock Top/Bottom ก่อน แล้วค่อย Left/Right
2. **LastChildFill**: ใช้ประโยชน์จาก Default behavior
3. **Nesting**: สามารถซ้อน DockPanel หรือใช้ร่วมกับ Panel อื่นได้
4. **Simplicity**: DockPanel เหมาะกับ Simple Layout ถ้าซับซ้อนให้ใช้ Grid

---

## Code Examples

### Example 1: IDE Layout
```xml
<DockPanel>
    <!-- Menu -->
    <Menu DockPanel.Dock="Top">
        <MenuItem Header="File"/>
        <MenuItem Header="Edit"/>
        <MenuItem Header="View"/>
    </Menu>
    
    <!-- Toolbar -->
    <ToolBar DockPanel.Dock="Top">
        <Button Content="New"/>
        <Button Content="Open"/>
        <Button Content="Save"/>
    </ToolBar>
    
    <!-- Status Bar -->
    <StatusBar DockPanel.Dock="Bottom">
        <TextBlock Text="Ready"/>
    </StatusBar>
    
    <!-- Solution Explorer -->
    <TreeView DockPanel.Dock="Right" Width="200"/>
    
    <!-- Code Editor -->
    <TextBox AcceptsReturn="True" FontFamily="Consolas"/>
</DockPanel>
```

### Example 2: Dashboard Layout
```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#2C3E50" Height="60">
        <TextBlock Text="Dashboard" FontSize="24" 
                   Foreground="White" Margin="20,0" 
                   VerticalAlignment="Center"/>
    </Border>
    
    <!-- Navigation -->
    <Border DockPanel.Dock="Left" Background="#34495E" Width="200">
        <StackPanel>
            <Button Content="📊 Overview" Height="50"/>
            <Button Content="📈 Analytics" Height="50"/>
            <Button Content="⚙️ Settings" Height="50"/>
        </StackPanel>
    </Border>
    
    <!-- Content -->
    <Grid Background="#ECF0F1" Margin="10">
        <!-- Dashboard widgets here -->
    </Grid>
</DockPanel>
```

### Example 3: Chat Application
```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#128C7E" Height="50">
        <TextBlock Text="Chat App" FontSize="18" 
                   Foreground="White" Margin="15,0" 
                   VerticalAlignment="Center"/>
    </Border>
    
    <!-- Chat List -->
    <Border DockPanel.Dock="Left" Background="White" 
            Width="250" BorderBrush="LightGray" 
            BorderThickness="0,0,1,0">
        <ListBox>
            <ListBoxItem Content="John Doe"/>
            <ListBoxItem Content="Jane Smith"/>
        </ListBox>
    </Border>
    
    <!-- Message Input -->
    <Border DockPanel.Dock="Bottom" Height="60" 
            Background="White" BorderBrush="LightGray" 
            BorderThickness="0,1,0,0">
        <Grid Margin="10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="Auto"/>
            </Grid.ColumnDefinitions>
            <TextBox Grid.Column="0" Margin="0,0,10,0"/>
            <Button Grid.Column="1" Content="Send" Width="80"/>
        </Grid>
    </Border>
    
    <!-- Messages -->
    <ScrollViewer Background="#ECE5DD">
        <StackPanel Margin="10">
            <!-- Chat messages here -->
        </StackPanel>
    </ScrollViewer>
</DockPanel>
```

---

## Common Mistakes (ข้อผิดพลาดที่พบบ่อย)

### ❌ ลืมใส่ Center Element
```xml
<!-- ผิด: ไม่มี Element ตรงกลาง -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
</DockPanel>
```

### ✅ ถูกต้อง
```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border Background="White"/>  <!-- Center -->
</DockPanel>
```

### ❌ Dock ทุก Element
```xml
<!-- ผิด: Dock ทุกตัว ไม่มีตัวที่เต็มตรงกลาง -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border DockPanel.Dock="Left" Width="100"/>
    <Border DockPanel.Dock="Right" Width="100"/>  <!-- ไม่มี Center -->
</DockPanel>
```

### ✅ ถูกต้อง
```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border DockPanel.Dock="Left" Width="100"/>
    <Border/>  <!-- Element สุดท้ายไม่ Dock = Center -->
</DockPanel>
```

---

## แบบฝึกหัด

### Exercise 1: สร้าง IDE Layout
สร้าง Layout คล้าย Visual Studio:
- Menu Bar ด้านบน
- Toolbar ด้านบนถัดลงมา
- Status Bar ด้านล่าง
- Solution Explorer ด้านขวา (Width 200)
- Properties Panel ด้านซ้าย (Width 180)
- Code Editor ตรงกลาง

### Exercise 2: สร้าง Email Client
สร้าง Email Client Layout:
- Header พร้อม Logo และ Search Box
- Folder List ด้านซ้าย (Inbox, Sent, Trash)
- Email List ถัดจาก Folder List
- Email Content ด้านขวาสุด

### Exercise 3: สร้าง Dashboard
สร้าง Admin Dashboard:
- Navigation Bar ด้านบน
- Sidebar Menu ด้านซ้าย
- Footer ด้านล่าง
- Main Content Area ใช้ Grid แสดง Widgets

---

## Code Examples Repository

Source code สำหรับ Episode นี้สามารถดาวน์โหลดได้ที่:
- GitHub: [WPF_Episode06_DockPanel](https://github.com/koson/WPF_Episode06_DockPanel)

---

**End of Script**