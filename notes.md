# Episode 06: DockPanel - Quick Reference

> 💡 **Core Concept**: Dock elements to edges (Top, Bottom, Left, Right) - perfect for application layouts!

---

## 🎯 The Problem DockPanel Solves

**Problem: Creating application layouts with Grid is tedious**
```xml
<!-- ❌ Grid requires row/column definitions for simple layouts -->
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="50"/>   <!-- Header -->
        <RowDefinition Height="*"/>    <!-- Content -->
        <RowDefinition Height="30"/>   <!-- Footer -->
    </Grid.RowDefinitions>
    
    <Border Grid.Row="0" Background="Blue"/>  <!-- Header -->
    <Border Grid.Row="1" Background="White"/> <!-- Content -->
    <Border Grid.Row="2" Background="Gray"/>  <!-- Footer -->
    <!-- What about sidebar? Need columns too! 😩 -->
</Grid>
```

**Solution: DockPanel!**
```xml
<!-- ✅ DockPanel is semantic and simple! -->
<DockPanel>
    <Border DockPanel.Dock="Top" Background="Blue" Height="50"/>
    <Border DockPanel.Dock="Bottom" Background="Gray" Height="30"/>
    <Border DockPanel.Dock="Left" Background="LightGray" Width="150"/>
    <Border Background="White"/>  <!-- Center fills remaining space! -->
</DockPanel>
```

**Benefits:**
- ✅ Clear and semantic (Dock="Top" = obviously at top!)
- ✅ No row/column calculations needed
- ✅ Perfect for app layouts (header, footer, sidebar)
- ✅ LastChildFill handles center automatically

---

## 📋 Basic Syntax

### Docking to Top
```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Header" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Docking to Bottom
```xml
<DockPanel>
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Footer" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Docking to Left
```xml
<DockPanel>
    <Border DockPanel.Dock="Left" Background="LightCoral" Width="150">
        <TextBlock Text="Sidebar" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Docking to Right
```xml
<DockPanel>
    <Border DockPanel.Dock="Right" Background="LightYellow" Width="100">
        <TextBlock Text="Panel" HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Complete Layout
```xml
<DockPanel>
    <!-- Top -->
    <Border DockPanel.Dock="Top" Background="LightBlue" Height="50">
        <TextBlock Text="Header"/>
    </Border>
    
    <!-- Bottom -->
    <Border DockPanel.Dock="Bottom" Background="LightGreen" Height="40">
        <TextBlock Text="Footer"/>
    </Border>
    
    <!-- Left -->
    <Border DockPanel.Dock="Left" Background="LightCoral" Width="150">
        <TextBlock Text="Sidebar"/>
    </Border>
    
    <!-- Right -->
    <Border DockPanel.Dock="Right" Background="LightYellow" Width="100">
        <TextBlock Text="Panel"/>
    </Border>
    
    <!-- Center (no Dock = LastChildFill) -->
    <Border Background="White">
        <TextBlock Text="Main Content" FontSize="24" 
                   HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

---

## 🔧 Essential Properties

### DockPanel.Dock (Attached Property)
```xml
DockPanel.Dock="Top"     <!-- Dock to top edge -->
DockPanel.Dock="Bottom"  <!-- Dock to bottom edge -->
DockPanel.Dock="Left"    <!-- Dock to left edge -->
DockPanel.Dock="Right"   <!-- Dock to right edge -->
```

### LastChildFill Property
```xml
<!-- Default: LastChildFill="True" -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border/>  <!-- Fills remaining space automatically! -->
</DockPanel>

<!-- LastChildFill="False" -->
<DockPanel LastChildFill="False">
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border/>  <!-- Uses its natural size, doesn't fill! -->
</DockPanel>
```

---

## ⚠️ Docking Order Matters!

### Order 1: Top → Left
```xml
<DockPanel>
    <Border DockPanel.Dock="Top" Background="Red" Height="50"/>
    <Border DockPanel.Dock="Left" Background="Blue" Width="100"/>
    <Border Background="White"/>
</DockPanel>
```

**Result:**
```
┌─────────────────────────┐
│        Top (Red)        │ ← Full width
├──────┬──────────────────┤
│ Left │                  │
│(Blue)│  Center (White)  │
│      │                  │
└──────┴──────────────────┘
```

### Order 2: Left → Top
```xml
<DockPanel>
    <Border DockPanel.Dock="Left" Background="Blue" Width="100"/>
    <Border DockPanel.Dock="Top" Background="Red" Height="50"/>
    <Border Background="White"/>
</DockPanel>
```

**Result:**
```
┌──────┬─────────────────┐
│      │  Top (Red)      │ ← Partial width
│ Left ├─────────────────┤
│(Blue)│                 │
│      │ Center (White)  │
│      │                 │
└──────┴─────────────────┘
↑ Full height
```

**Rule:** Element that docks first gets full dimension!

---

## 💡 Common Patterns

### Pattern 1: Application Window Layout
```xml
<DockPanel>
    <!-- Header -->
    <Border DockPanel.Dock="Top" Background="#4A90E2" Height="50">
        <TextBlock Text="Header / Menu Bar" FontSize="20" Foreground="White" 
                   VerticalAlignment="Center" HorizontalAlignment="Center"/>
    </Border>
    
    <!-- Footer -->
    <Border DockPanel.Dock="Bottom" Background="#34495E" Height="40">
        <TextBlock Text="Footer / Status Bar" FontSize="14" Foreground="White" 
                   VerticalAlignment="Center" HorizontalAlignment="Center"/>
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
    
    <!-- Main Content -->
    <Border Background="White">
        <TextBlock Text="Main Content Area" FontSize="24" 
                   HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Pattern 2: IDE Layout (Visual Studio Style)
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
    
    <!-- Solution Explorer (Right) -->
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

### Pattern 3: Browser Layout
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
            <TextBox Grid.Column="1" Text="https://example.com" 
                     VerticalContentAlignment="Center" Margin="5,0"/>
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
                   HorizontalAlignment="Center" VerticalAlignment="Center"/>
    </Border>
</DockPanel>
```

### Pattern 4: Email Client Layout
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
    <Border DockPanel.Dock="Left" Background="White" Width="250" 
            BorderBrush="LightGray" BorderThickness="0,0,1,0">
        <StackPanel Margin="10">
            <TextBlock Text="Messages" FontWeight="Bold" Margin="0,0,0,10"/>
            <Border Background="LightBlue" Padding="10" Margin="0,5">
                <TextBlock Text="Meeting Tomorrow"/>
            </Border>
            <Border Background="White" Padding="10" Margin="0,5" 
                    BorderBrush="LightGray" BorderThickness="1">
                <TextBlock Text="Project Update"/>
            </Border>
        </StackPanel>
    </Border>
    
    <!-- Email Content -->
    <Border Background="White" Padding="20">
        <TextBlock Text="Email content will be displayed here" TextWrapping="Wrap"/>
    </Border>
</DockPanel>
```

---

## ⚠️ Common Problems & Solutions

### Problem 1: Forgot Center Element
```xml
<!-- ❌ Problem: No center element, empty space in middle -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <!-- Missing center! -->
</DockPanel>

<!-- ✅ Solution: Always add center element -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border Background="White"/>  <!-- Center! -->
</DockPanel>
```

### Problem 2: Docked All Elements
```xml
<!-- ❌ Problem: All elements docked, LastChildFill has nothing to fill -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border DockPanel.Dock="Left" Width="100"/>
    <Border DockPanel.Dock="Right" Width="100"/>
    <!-- All docked! No center element! -->
</DockPanel>

<!-- ✅ Solution: Last element should NOT be docked -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border DockPanel.Dock="Left" Width="100"/>
    <Border/>  <!-- This fills center! -->
</DockPanel>
```

### Problem 3: Wrong Docking Order
```xml
<!-- ❌ Problem: Left docks first, takes full height -->
<DockPanel>
    <Border DockPanel.Dock="Left" Width="100"/>
    <Border DockPanel.Dock="Top" Height="50"/>
    <!-- Top doesn't span full width! -->
</DockPanel>

<!-- ✅ Solution: Dock Top/Bottom first for full width -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>  <!-- Full width! -->
    <Border DockPanel.Dock="Left" Width="100"/>
</DockPanel>
```

---

## 🎨 DockPanel vs Grid

### Use DockPanel When:
```xml
<!-- ✅ Simple edge-docking layout -->
<DockPanel>
    <Border DockPanel.Dock="Top" Height="50"/>
    <Border DockPanel.Dock="Bottom" Height="30"/>
    <Border/>
</DockPanel>
```

✅ **Application layouts** (header, footer, sidebar)  
✅ **Clear semantic meaning** (Dock="Top" = obviously top!)  
✅ **Simple edge positioning**  
✅ **No complex row/column math needed**

### Use Grid When:
```xml
<!-- ✅ Complex multi-row/column layout -->
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <!-- Proportional sizing, spanning, etc. -->
</Grid>
```

✅ **Complex table layouts**  
✅ **Need proportional sizing** (Star *)  
✅ **Need row/column spanning**  
✅ **Overlapping elements**

---

## 📊 Quick Comparison

| Feature | DockPanel | Grid | StackPanel |
|---------|-----------|------|------------|
| **Purpose** | Edge docking | Table layout | Linear stacking |
| **Semantic** | ✅ Very clear | ⚠️ Row/column indices | ✅ Clear |
| **Complexity** | Simple | Medium | Simple |
| **Best For** | App layouts | Complex forms | Menus, lists |
| **Responsive** | ✅ Yes | ✅ Yes | ⚠️ Limited |

---

## ✅ Best Practices

### Do's ✅
1. **Dock Top/Bottom first** for full width
   ```xml
   <DockPanel>
       <Border DockPanel.Dock="Top"/>    <!-- 1st: Full width -->
       <Border DockPanel.Dock="Bottom"/> <!-- 2nd: Full width -->
       <Border DockPanel.Dock="Left"/>   <!-- 3rd: Remaining height -->
   </DockPanel>
   ```

2. **Last element should NOT be docked** (let LastChildFill work)
   ```xml
   <DockPanel>
       <Border DockPanel.Dock="Top"/>
       <Border/>  <!-- No Dock! -->
   </DockPanel>
   ```

3. **Combine with other panels**
   ```xml
   <DockPanel>
       <Border DockPanel.Dock="Top">
           <StackPanel Orientation="Horizontal">
               <!-- Toolbar buttons -->
           </StackPanel>
       </Border>
   </DockPanel>
   ```

### Don'ts ❌
1. **Don't forget center element**
2. **Don't dock all elements**
3. **Don't use when Grid is more appropriate** (complex layouts)
4. **Don't set LastChildFill="True"** (it's default, unnecessary)

---

## 💻 Code Behind Tips

### Adding Elements Dynamically
```csharp
// Create element
Border border = new Border
{
    Background = Brushes.LightBlue,
    Height = 50
};

// Set dock position
DockPanel.SetDock(border, Dock.Top);

// Add to DockPanel
MyDockPanel.Children.Add(border);
```

### Getting Dock Value
```csharp
Dock dock = DockPanel.GetDock(myBorder);
// Returns: Dock.Top, Dock.Bottom, Dock.Left, or Dock.Right
```

### Setting LastChildFill
```csharp
MyDockPanel.LastChildFill = false;
```

---

## 📝 Key Takeaways

✅ **DockPanel** = Dock to edges (Top, Bottom, Left, Right)  
✅ **Semantic and clear** - Dock="Top" obviously means top!  
✅ **Perfect for app layouts** - Header, Footer, Sidebar, Content  
✅ **LastChildFill** - Last element fills remaining space  
✅ **Order matters** - First docked gets full dimension  
✅ **Combine with other panels** - StackPanel inside DockPanel  
⚠️ **Not for complex layouts** - Use Grid instead  
⚠️ **Remember center element** - Don't dock everything!

---

## 🎯 When to Use DockPanel

### ✅ Perfect For:
- **Application main window** (header, footer, sidebar)
- **IDE layouts** (menu, toolbar, status bar, panels)
- **Browser layouts** (address bar, bookmarks, content)
- **Email clients** (toolbar, folder list, message list, content)
- **Dashboards** (navigation, content areas)

### ❌ Don't Use For:
- **Complex table layouts** (use Grid)
- **Forms with many fields** (use Grid)
- **Simple vertical lists** (use StackPanel)
- **Need proportional sizing** (use Grid with Star *)

---

## 🔗 Related Topics

- **Previous**: Episode 05 - WrapPanel (wrapping layouts)
- **Alternative**: Episode 04 - Grid (table layouts)
- **Next**: Episode 07 - Canvas (absolute positioning)
- **Complement**: Episode 03 - StackPanel (linear stacking)

---

## 📚 Resources

- [Complete Guide](README.md) - Detailed documentation
- [Tutorial Script](YouTube-Script.md) - Full 42-minute script
- [Official Docs](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.dockpanel)

---

**Quick Reference Version 1.0** | Last Updated: November 25, 2025
