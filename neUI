local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local Lighting = game:GetService("Lighting")
local MarketplaceService = game:GetService("MarketplaceService")
local HttpService = game:GetService("HttpService")
local CoreGui = game:GetService("CoreGui")
local LocalPlayer = Players.LocalPlayer
local WindIcons = nil
task.spawn(function()
    pcall(function()
        WindIcons = loadstring(game:HttpGet("https://raw.githubusercontent.com/Footagesus/Icons/main/Main.lua"))()
        if WindIcons and WindIcons.SetIconsType then
            WindIcons.SetIconsType("lucide")
        end
    end)
end)
local FallbackLucide = {
    ["info"] = "rbxassetid://10723415903",
    ["home"] = "rbxassetid://10723407389",
    ["settings"] = "rbxassetid://10734950309",
    ["sliders"] = "rbxassetid://10734963400",
    ["user"] = "rbxassetid://10747373176",
    ["users"] = "rbxassetid://10747373426",
    ["search"] = "rbxassetid://10734943674",
    ["check"] = "rbxassetid://10709790644",
    ["chevron-down"] = "rbxassetid://10709790948",
    ["chevron-right"] = "rbxassetid://10709791437",
    ["sparkles"] = "rbxassetid://10734966248",
    ["zap"] = "rbxassetid://10747384394",
    ["shield"] = "rbxassetid://10734951847",
    ["eye"] = "rbxassetid://10723346959",
    ["map-pin"] = "rbxassetid://10723426886",
    ["compass"] = "rbxassetid://10709811445",
    ["shopping-bag"] = "rbxassetid://10734952479",
    ["palette"] = "rbxassetid://10734910430",
    ["cpu"] = "rbxassetid://10709813383",
    ["activity"] = "rbxassetid://10709752035",
    ["globe"] = "rbxassetid://10723404337",
    ["terminal"] = "rbxassetid://10734982144",
    ["bell"] = "rbxassetid://10709775704",
    ["layers"] = "rbxassetid://10723424505",
    ["award"] = "rbxassetid://10709769841",
    ["x"] = "rbxassetid://10747384394",
    ["minus"] = "rbxassetid://10723435615"
}
local function ApplyWindIcon(imageLabel, iconName)
    if not imageLabel or not iconName or iconName == "" then return end
    if string.find(iconName, "rbxassetid://") or string.find(iconName, "rbxthumb://") then
        imageLabel.Image = iconName
        imageLabel.ImageRectSize = Vector2.zero
        imageLabel.ImageRectOffset = Vector2.zero
        return
    end
    local cleanName = string.lower(string.gsub(iconName, "^lucide%-", ""))
    if WindIcons and WindIcons.Icon then
        local ok, iconData = pcall(function() return WindIcons.Icon(cleanName, "lucide") end)
        if ok and iconData then
            if type(iconData) == "table" then
                imageLabel.Image = iconData[1] or ""
                if iconData[2] then
                    imageLabel.ImageRectSize = iconData[2].ImageRectSize or Vector2.zero
                    imageLabel.ImageRectOffset = iconData[2].ImageRectOffset or Vector2.zero
                end
                return
            elseif type(iconData) == "string" then
                imageLabel.Image = iconData
                return
            end
        end
    end
    imageLabel.Image = FallbackLucide[cleanName] or FallbackLucide["sparkles"]
end
local FontStyles = {
    ["Normal"] = {
        Regular = Font.fromEnum(Enum.Font.Gotham),
        Medium = Font.fromEnum(Enum.Font.GothamMedium),
        Bold = Font.fromEnum(Enum.Font.GothamBold),
        Mono = Font.fromEnum(Enum.Font.Code)
    },
    ["Minecraft"] = {
        Regular = Font.fromEnum(Enum.Font.Arcade),
        Medium = Font.fromEnum(Enum.Font.Arcade),
        Bold = Font.fromEnum(Enum.Font.Arcade),
        Mono = Font.fromEnum(Enum.Font.Arcade)
    }
}
local Themes = {
    ["Liquid Glass"] = {
        WindowBg = Color3.fromRGB(14, 16, 26),
        WindowTrans = 0.24,
        SidebarBg = Color3.fromRGB(20, 23, 36),
        SidebarTrans = 0.36,
        CardBg = Color3.fromRGB(28, 33, 50),
        CardTrans = 0.3,
        CardHover = Color3.fromRGB(38, 45, 68),
        InputBg = Color3.fromRGB(16, 20, 32),
        InputTrans = 0.22,
        Accent = Color3.fromRGB(95, 215, 255),
        AccentSecondary = Color3.fromRGB(165, 115, 255),
        Text = Color3.fromRGB(245, 248, 255),
        SubText = Color3.fromRGB(165, 178, 205),
        Stroke = Color3.fromRGB(185, 225, 255),
        StrokeTrans = 0.6,
        UseBlur = true
    },
    ["Dark"] = {
        WindowBg = Color3.fromRGB(12, 13, 19),
        WindowTrans = 0.03,
        SidebarBg = Color3.fromRGB(17, 18, 26),
        SidebarTrans = 0.04,
        CardBg = Color3.fromRGB(23, 25, 35),
        CardTrans = 0.04,
        CardHover = Color3.fromRGB(31, 34, 47),
        InputBg = Color3.fromRGB(15, 16, 23),
        InputTrans = 0.04,
        Accent = Color3.fromRGB(99, 102, 241),
        AccentSecondary = Color3.fromRGB(139, 92, 246),
        Text = Color3.fromRGB(242, 244, 250),
        SubText = Color3.fromRGB(145, 150, 172),
        Stroke = Color3.fromRGB(52, 56, 76),
        StrokeTrans = 0.35,
        UseBlur = false
    },
    ["White"] = {
        WindowBg = Color3.fromRGB(242, 245, 250),
        WindowTrans = 0.06,
        SidebarBg = Color3.fromRGB(232, 236, 244),
        SidebarTrans = 0.1,
        CardBg = Color3.fromRGB(255, 255, 255),
        CardTrans = 0.05,
        CardHover = Color3.fromRGB(245, 248, 255),
        InputBg = Color3.fromRGB(236, 240, 248),
        InputTrans = 0.05,
        Accent = Color3.fromRGB(37, 99, 235),
        AccentSecondary = Color3.fromRGB(79, 70, 229),
        Text = Color3.fromRGB(20, 24, 36),
        SubText = Color3.fromRGB(100, 110, 135),
        Stroke = Color3.fromRGB(205, 214, 230),
        StrokeTrans = 0.25,
        UseBlur = true
    },
    ["Rose"] = {
        WindowBg = Color3.fromRGB(22, 12, 18),
        WindowTrans = 0.14,
        SidebarBg = Color3.fromRGB(30, 16, 24),
        SidebarTrans = 0.2,
        CardBg = Color3.fromRGB(40, 21, 32),
        CardTrans = 0.18,
        CardHover = Color3.fromRGB(54, 28, 43),
        InputBg = Color3.fromRGB(25, 13, 20),
        InputTrans = 0.1,
        Accent = Color3.fromRGB(244, 63, 94),
        AccentSecondary = Color3.fromRGB(251, 113, 133),
        Text = Color3.fromRGB(255, 241, 244),
        SubText = Color3.fromRGB(205, 155, 170),
        Stroke = Color3.fromRGB(244, 63, 94),
        StrokeTrans = 0.65,
        UseBlur = true
    },
    ["Purple"] = {
        WindowBg = Color3.fromRGB(16, 11, 26),
        WindowTrans = 0.14,
        SidebarBg = Color3.fromRGB(23, 16, 36),
        SidebarTrans = 0.2,
        CardBg = Color3.fromRGB(32, 22, 50),
        CardTrans = 0.18,
        CardHover = Color3.fromRGB(44, 30, 68),
        InputBg = Color3.fromRGB(20, 14, 32),
        InputTrans = 0.1,
        Accent = Color3.fromRGB(168, 85, 247),
        AccentSecondary = Color3.fromRGB(217, 70, 239),
        Text = Color3.fromRGB(248, 242, 255),
        SubText = Color3.fromRGB(178, 155, 210),
        Stroke = Color3.fromRGB(168, 85, 247),
        StrokeTrans = 0.65,
        UseBlur = true
    },
    ["Cyan"] = {
        WindowBg = Color3.fromRGB(10, 20, 26),
        WindowTrans = 0.14,
        SidebarBg = Color3.fromRGB(14, 28, 36),
        SidebarTrans = 0.2,
        CardBg = Color3.fromRGB(19, 38, 49),
        CardTrans = 0.18,
        CardHover = Color3.fromRGB(26, 50, 64),
        InputBg = Color3.fromRGB(12, 24, 31),
        InputTrans = 0.1,
        Accent = Color3.fromRGB(6, 182, 212),
        AccentSecondary = Color3.fromRGB(56, 189, 248),
        Text = Color3.fromRGB(236, 254, 255),
        SubText = Color3.fromRGB(148, 198, 215),
        Stroke = Color3.fromRGB(34, 211, 238),
        StrokeTrans = 0.65,
        UseBlur = true
    }
}
local function Tween(obj, time, style, dir, props)
    if not obj then return end
    local t = TweenService:Create(obj, TweenInfo.new(time or 0.24, style or Enum.EasingStyle.Quart, dir or Enum.EasingDirection.Out), props)
    t:Play()
    return t
end
local function Create(className, props, children)
    local inst = Instance.new(className)
    for k, v in pairs(props or {}) do
        if k ~= "Parent" then inst[k] = v end
    end
    for _, child in ipairs(children or {}) do
        child.Parent = inst
    end
    if props and props.Parent then inst.Parent = props.Parent end
    return inst
end
local function RippleEffect(btn, accentColor)
    btn.ClipsDescendants = true
    btn.InputBegan:Connect(function(inp)
        if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
            local relX = inp.Position.X - btn.AbsolutePosition.X
            local relY = inp.Position.Y - btn.AbsolutePosition.Y
            local circle = Create("Frame", {
                AnchorPoint = Vector2.new(0.5, 0.5),
                Position = UDim2.new(0, relX, 0, relY),
                Size = UDim2.new(0, 0, 0, 0),
                BackgroundColor3 = accentColor or Color3.fromRGB(255, 255, 255),
                BackgroundTransparency = 0.68,
                ZIndex = btn.ZIndex + 2,
                Parent = btn
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local maxDim = math.max(btn.AbsoluteSize.X, btn.AbsoluteSize.Y) * 2.2
            Tween(circle, 0.45, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {
                Size = UDim2.new(0, maxDim, 0, maxDim),
                BackgroundTransparency = 1
            })
            task.delay(0.46, function()
                if circle then circle:Destroy() end
            end)
        end
    end)
end
local function MakeDraggable(handle, target, uiScaleObj)
    local dragging, dragInput, dragStart, startPos = false, nil, nil, nil
    handle.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            dragging = true
            dragStart = input.Position
            startPos = target.Position
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then dragging = false end
            end)
        end
    end)
    handle.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
            dragInput = input
        end
    end)
    UserInputService.InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            local delta = input.Position - dragStart
            local cam = workspace.CurrentCamera
            local vp = cam and cam.ViewportSize or Vector2.new(1920, 1080)
            local scale = (uiScaleObj and uiScaleObj.Scale) or 1
            local halfW = (target.Size.X.Offset * scale) * 0.5
            local halfH = (target.Size.Y.Offset * scale) * 0.5
            local rawX = (startPos.X.Scale * vp.X) + startPos.X.Offset + delta.X
            local rawY = (startPos.Y.Scale * vp.Y) + startPos.Y.Offset + delta.Y
            local clampedX = math.clamp(rawX, math.min(halfW + 6, vp.X * 0.5), math.max(vp.X - halfW - 6, vp.X * 0.5))
            local clampedY = math.clamp(rawY, math.min(halfH + 6, vp.Y * 0.5), math.max(vp.Y - halfH - 6, vp.Y * 0.5))
            Tween(target, 0.08, Enum.EasingStyle.Sine, Enum.EasingDirection.Out, {
                Position = UDim2.new(0, clampedX, 0, clampedY)
            })
        end
    end)
end
local GlassLib = {}
GlassLib.__index = GlassLib
GlassLib.Themes = {"Liquid Glass", "Dark", "White", "Rose", "Purple", "Cyan"}
GlassLib.Fonts = {"Minecraft", "Normal"}
function GlassLib:CreateWindow(cfg)
    cfg = cfg or {}
    local TitleText = tostring(cfg.Title or "Dynex Hub")
    local SubTitleText = tostring(cfg.SubTitle or "Liquid Glass Pro v4.2")
    local WinSize = cfg.Size or UDim2.new(0, 680, 0, 440)
    local MinimizeKey = cfg.MinimizeKey or Enum.KeyCode.RightControl
    local CurrentThemeName = cfg.Theme and Themes[cfg.Theme] and cfg.Theme or "Rose"
    local CurrentToggleStyle = (cfg.ToggleStyle == "Checkbox") and "Checkbox" or "Switch"
    local CurrentFontMode = (cfg.Font == "Normal" or cfg.FontStyle == "Normal") and "Normal" or "Minecraft"
    local AutoScaleEnabled = (cfg.AutoResize ~= false)
    local ConfigFolder = tostring(cfg.ConfigFolder or "DN_AetherConfigs")
    local Theme = Themes[CurrentThemeName]
    local parentGui = (gethui and gethui()) or CoreGui
    pcall(function()
        if parentGui:FindFirstChild("DN_LiquidGlassUI") then parentGui.DN_LiquidGlassUI:Destroy() end
        if Lighting:FindFirstChild("DN_LiquidBlur") then Lighting.DN_LiquidBlur:Destroy() end
    end)
    local ScreenGui = Create("ScreenGui", {
        Name = "DN_LiquidGlassUI",
        ZIndexBehavior = Enum.ZIndexBehavior.Sibling,
        IgnoreGuiInset = false,
        ResetOnSpawn = false
    })
    if not pcall(function() ScreenGui.Parent = parentGui end) then
        ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")
    end
    local BlurObj = Create("BlurEffect", {
        Name = "DN_LiquidBlur",
        Size = Theme.UseBlur and 12 or 0,
        Parent = Lighting
    })
    local Window = {
        _themeName = CurrentThemeName,
        _theme = Theme,
        _toggleStyle = CurrentToggleStyle,
        _fontMode = CurrentFontMode,
        _fontRegistry = setmetatable({}, {__mode = "k"}),
        _themeListeners = {},
        _toggleStyleListeners = {},
        _fontListeners = {},
        _tabs = {},
        _activeTab = nil,
        _minimized = false,
        _baseWidth = WinSize.X.Offset,
        _baseHeight = WinSize.Y.Offset,
        _flags = {},
        _flagSetters = {},
        _keybinds = {},
        _allSearchItems = {},
        _configFolder = ConfigFolder
    }
    local function BindFont(obj, weight)
        if not obj then return obj end
        local w = weight or "Regular"
        Window._fontRegistry[obj] = w
        local pack = FontStyles[Window._fontMode] or FontStyles["Minecraft"]
        pcall(function() obj.FontFace = pack[w] or pack.Regular end)
        return obj
    end
    function Window:SetFontStyle(mode)
        self._fontMode = (mode == "Normal") and "Normal" or "Minecraft"
        local pack = FontStyles[self._fontMode]
        for obj, w in pairs(self._fontRegistry) do
            if obj and obj.Parent then
                pcall(function() obj.FontFace = pack[w] or pack.Regular end)
            end
        end
        for _, fn in ipairs(self._fontListeners) do
            task.spawn(fn, self._fontMode)
        end
    end
    Window.SetFont = Window.SetFontStyle
    function Window:OnThemeChange(fn)
        table.insert(self._themeListeners, fn)
        task.spawn(fn, self._theme, self._themeName)
    end
    function Window:SetTheme(themeName)
        if not Themes[themeName] then return end
        self._themeName = themeName
        self._theme = Themes[themeName]
        Tween(BlurObj, 0.35, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {
            Size = (not self._minimized and self._theme.UseBlur) and 12 or 0
        })
        for _, fn in ipairs(self._themeListeners) do
            task.spawn(fn, self._theme, themeName)
        end
    end
    function Window:SetToggleStyle(style)
        self._toggleStyle = (style == "Checkbox") and "Checkbox" or "Switch"
        for _, fn in ipairs(self._toggleStyleListeners) do
            task.spawn(fn, self._toggleStyle)
        end
    end
    function Window:SaveConfig(profileName)
        local name = tostring(profileName or "default")
        pcall(function()
            if isfolder and makefolder and writefile then
                if not isfolder(self._configFolder) then makefolder(self._configFolder) end
                writefile(self._configFolder .. "/" .. name .. ".json", HttpService:JSONEncode(self._flags))
            end
        end)
    end
    function Window:LoadConfig(profileName)
        local name = tostring(profileName or "default")
        pcall(function()
            if isfile and readfile then
                local path = self._configFolder .. "/" .. name .. ".json"
                if isfile(path) then
                    local data = HttpService:JSONDecode(readfile(path))
                    if type(data) == "table" then
                        for k, v in pairs(data) do
                            self._flags[k] = v
                            if self._flagSetters[k] then
                                pcall(self._flagSetters[k], v)
                            end
                        end
                    end
                end
            end
        end)
    end
    local DynamicIsland = Create("TextButton", {
        Name = "DynamicIsland",
        AnchorPoint = Vector2.new(0.5, 0),
        Size = UDim2.new(0, 320, 0, 32),
        Position = UDim2.new(0.5, 0, 0, 8),
        BackgroundColor3 = Theme.WindowBg,
        BackgroundTransparency = 0.12,
        Text = "",
        AutoButtonColor = false,
        Parent = ScreenGui
    }, {
        Create("UICorner", {CornerRadius = UDim.new(1, 0)})
    })
    local IslandScale = Create("UIScale", {Scale = 1, Parent = DynamicIsland})
    local IslandStroke = Create("UIStroke", {
        Color = Theme.Accent,
        Thickness = 1.2,
        Transparency = 0.25,
        Parent = DynamicIsland
    })
    MakeDraggable(DynamicIsland, DynamicIsland, IslandScale)
    local IslandDot = BindFont(Create("TextLabel", {
        Size = UDim2.new(0, 62, 1, 0),
        Position = UDim2.new(0, 12, 0, 0),
        BackgroundTransparency = 1,
        Text = "● LIVE",
        TextSize = 11,
        TextColor3 = Theme.Accent,
        TextXAlignment = Enum.TextXAlignment.Left,
        Parent = DynamicIsland
    }), "Bold")
    local IslandTitle = BindFont(Create("TextLabel", {
        Size = UDim2.new(1, -165, 1, 0),
        Position = UDim2.new(0, 72, 0, 0),
        BackgroundTransparency = 1,
        Text = TitleText,
        TextSize = 12,
        TextColor3 = Theme.Text,
        TextXAlignment = Enum.TextXAlignment.Left,
        TextTruncate = Enum.TextTruncate.AtEnd,
        Parent = DynamicIsland
    }), "Bold")
    local IslandTelemetry = BindFont(Create("TextLabel", {
        Size = UDim2.new(0, 88, 1, 0),
        Position = UDim2.new(1, -98, 0, 0),
        BackgroundTransparency = 1,
        Text = "60 FPS | 00:00",
        TextSize = 11,
        TextColor3 = Theme.SubText,
        TextXAlignment = Enum.TextXAlignment.Right,
        Parent = DynamicIsland
    }), "Mono")
    Window._islandTitle = IslandTitle
    Window._islandMark = IslandDot
    Window._islandMono = IslandTelemetry
    function Window:SetTask(info)
        if type(info) == "table" and info.Current then
            IslandTitle.Text = tostring(info.Current)
        end
    end
    local startClock = os.clock()
    task.spawn(function()
        while ScreenGui.Parent do
            local dt = RunService.RenderStepped:Wait()
            local fps = math.clamp(math.floor(1 / math.max(0.001, dt)), 1, 999)
            local elapsed = math.floor(os.clock() - startClock)
            IslandTelemetry.Text = string.format("%d FPS | %02d:%02d", fps, math.floor(elapsed / 60), elapsed % 60)
            task.wait(0.6)
        end
    end)
    local MainFrame = Create("Frame", {
        Name = "MainWindow",
        AnchorPoint = Vector2.new(0.5, 0.5),
        Size = WinSize,
        Position = UDim2.new(0.5, 0, 0.52, 0),
        BackgroundColor3 = Theme.WindowBg,
        BackgroundTransparency = Theme.WindowTrans,
        ClipsDescendants = true,
        Parent = ScreenGui
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 14)})
    })
    local WindowScale = Create("UIScale", {
        Scale = 1,
        Parent = MainFrame
    })
    local MainStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1.3,
        Transparency = Theme.StrokeTrans,
        Parent = MainFrame
    }, {
        Create("UIGradient", {
            Rotation = 35,
            Transparency = NumberSequence.new({
                NumberSequenceKeypoint.new(0, 0.05),
                NumberSequenceKeypoint.new(0.5, 0.65),
                NumberSequenceKeypoint.new(1, 0.1)
            })
        })
    })
    Create("Frame", {
        Size = UDim2.new(1, 0, 1, 0),
        BackgroundColor3 = Color3.fromRGB(255, 255, 255),
        BackgroundTransparency = 0.94,
        ZIndex = 0,
        Parent = MainFrame
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 14)}),
        Create("UIGradient", {
            Rotation = 45,
            Color = ColorSequence.new({
                ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
                ColorSequenceKeypoint.new(0.45, Color3.fromRGB(180, 220, 255)),
                ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 0, 0))
            }),
            Transparency = NumberSequence.new({
                NumberSequenceKeypoint.new(0, 0.86),
                NumberSequenceKeypoint.new(0.5, 0.96),
                NumberSequenceKeypoint.new(1, 1)
            })
        })
    })
    local Topbar = Create("Frame", {
        Size = UDim2.new(1, 0, 0, 48),
        BackgroundTransparency = 1,
        Parent = MainFrame
    })
    MakeDraggable(Topbar, MainFrame, WindowScale)
    local TopLogo = Create("ImageLabel", {
        Size = UDim2.new(0, 20, 0, 20),
        Position = UDim2.new(0, 16, 0.5, -10),
        BackgroundTransparency = 1,
        ImageColor3 = Theme.Accent,
        Parent = Topbar
    })
    ApplyWindIcon(TopLogo, cfg.Icon or "sparkles")
    local TitleLbl = BindFont(Create("TextLabel", {
        Size = UDim2.new(0, 175, 0, 18),
        Position = UDim2.new(0, 44, 0, 8),
        BackgroundTransparency = 1,
        Text = TitleText,
        TextSize = 14,
        TextColor3 = Theme.Text,
        TextXAlignment = Enum.TextXAlignment.Left,
        TextTruncate = Enum.TextTruncate.AtEnd,
        Parent = Topbar
    }), "Bold")
    local SubTitleLbl = BindFont(Create("TextLabel", {
        Size = UDim2.new(0, 175, 0, 13),
        Position = UDim2.new(0, 44, 0, 26),
        BackgroundTransparency = 1,
        Text = SubTitleText,
        TextSize = 10,
        TextColor3 = Theme.SubText,
        TextXAlignment = Enum.TextXAlignment.Left,
        TextTruncate = Enum.TextTruncate.AtEnd,
        Parent = Topbar
    }), "Regular")
    local SearchBar = Create("Frame", {
        Size = UDim2.new(0, 185, 0, 30),
        Position = UDim2.new(1, -430, 0.5, -15),
        BackgroundColor3 = Theme.InputBg,
        BackgroundTransparency = Theme.InputTrans,
        Parent = Topbar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 8)})
    })
    local SearchStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = SearchBar
    })
    local SearchIcon = Create("ImageLabel", {
        Size = UDim2.new(0, 14, 0, 14),
        Position = UDim2.new(0, 9, 0.5, -7),
        BackgroundTransparency = 1,
        ImageColor3 = Theme.SubText,
        Parent = SearchBar
    })
    ApplyWindIcon(SearchIcon, "search")
    local SearchInput = BindFont(Create("TextBox", {
        Size = UDim2.new(1, -30, 1, 0),
        Position = UDim2.new(0, 27, 0, 0),
        BackgroundTransparency = 1,
        PlaceholderText = "Search (Ctrl+K)...",
        PlaceholderColor3 = Theme.SubText,
        Text = "",
        TextSize = 11,
        TextColor3 = Theme.Text,
        TextXAlignment = Enum.TextXAlignment.Left,
        ClearTextOnFocus = false,
        Parent = SearchBar
    }), "Regular")
    local FontQuickBtn = BindFont(Create("TextButton", {
        Size = UDim2.new(0, 74, 0, 30),
        Position = UDim2.new(1, -238, 0.5, -15),
        BackgroundColor3 = Theme.CardBg,
        BackgroundTransparency = Theme.CardTrans,
        Text = CurrentFontMode == "Minecraft" and "Aa Pixel" or "Aa Normal",
        TextSize = 11,
        TextColor3 = Theme.Accent,
        AutoButtonColor = false,
        Parent = Topbar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 8)})
    }), "Medium")
    local FontQuickStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = FontQuickBtn
    })
    FontQuickBtn.MouseButton1Click:Connect(function()
        local nextFont = (Window._fontMode == "Minecraft") and "Normal" or "Minecraft"
        Window:SetFontStyle(nextFont)
        Window:Notify({
            Title = "Font Changed",
            Content = "Đã đổi font thành: " .. nextFont,
            Duration = 2
        })
    end)
    table.insert(Window._fontListeners, function(fMode)
        FontQuickBtn.Text = (fMode == "Minecraft") and "Aa Pixel" or "Aa Normal"
    end)
    local StyleQuickBtn = BindFont(Create("TextButton", {
        Size = UDim2.new(0, 84, 0, 30),
        Position = UDim2.new(1, -158, 0.5, -15),
        BackgroundColor3 = Theme.CardBg,
        BackgroundTransparency = Theme.CardTrans,
        Text = CurrentToggleStyle == "Switch" and "● Switch" or "☑ Checkbox",
        TextSize = 11,
        TextColor3 = Theme.Text,
        AutoButtonColor = false,
        Parent = Topbar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 8)})
    }), "Medium")
    local StyleQuickStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = StyleQuickBtn
    })
    StyleQuickBtn.MouseButton1Click:Connect(function()
        local nextStyle = (Window._toggleStyle == "Switch") and "Checkbox" or "Switch"
        Window:SetToggleStyle(nextStyle)
    end)
    table.insert(Window._toggleStyleListeners, function(st)
        StyleQuickBtn.Text = (st == "Switch") and "● Switch" or "☑ Checkbox"
    end)
    local ThemeQuickBtn = Create("TextButton", {
        Size = UDim2.new(0, 30, 0, 30),
        Position = UDim2.new(1, -68, 0.5, -15),
        BackgroundColor3 = Theme.CardBg,
        BackgroundTransparency = Theme.CardTrans,
        Text = "",
        AutoButtonColor = false,
        Parent = Topbar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 8)})
    })
    local ThemeQuickStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = ThemeQuickBtn
    })
    local ThemeQuickIcon = Create("ImageLabel", {
        Size = UDim2.new(0, 15, 0, 15),
        Position = UDim2.new(0.5, -7.5, 0.5, -7.5),
        BackgroundTransparency = 1,
        ImageColor3 = Theme.Accent,
        Parent = ThemeQuickBtn
    })
    ApplyWindIcon(ThemeQuickIcon, "palette")
    ThemeQuickBtn.MouseButton1Click:Connect(function()
        local idx = table.find(GlassLib.Themes, Window._themeName) or 1
        local nextTheme = GlassLib.Themes[(idx % #GlassLib.Themes) + 1]
        Window:SetTheme(nextTheme)
        Window:Notify({
            Title = "Theme Switched",
            Content = "Active Theme: " .. nextTheme,
            Duration = 2.5
        })
    end)
    local MinBtn = Create("TextButton", {
        Size = UDim2.new(0, 30, 0, 30),
        Position = UDim2.new(1, -34, 0.5, -15),
        BackgroundColor3 = Theme.CardBg,
        BackgroundTransparency = Theme.CardTrans,
        Text = "",
        AutoButtonColor = false,
        Parent = Topbar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 8)})
    })
    local MinBtnStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = MinBtn
    })
    local XBar1 = Create("Frame", {
        AnchorPoint = Vector2.new(0.5, 0.5),
        Position = UDim2.new(0.5, 0, 0.5, 0),
        Size = UDim2.new(0, 13, 0, 2),
        Rotation = 45,
        BackgroundColor3 = Theme.Text,
        BorderSizePixel = 0,
        Parent = MinBtn
    }, {
        Create("UICorner", {CornerRadius = UDim.new(1, 0)})
    })
    local XBar2 = Create("Frame", {
        AnchorPoint = Vector2.new(0.5, 0.5),
        Position = UDim2.new(0.5, 0, 0.5, 0),
        Size = UDim2.new(0, 13, 0, 2),
        Rotation = -45,
        BackgroundColor3 = Theme.Text,
        BorderSizePixel = 0,
        Parent = MinBtn
    }, {
        Create("UICorner", {CornerRadius = UDim.new(1, 0)})
    })
    MinBtn.MouseEnter:Connect(function()
        Tween(XBar1, 0.15, nil, nil, {BackgroundColor3 = Theme.Accent, Rotation = 135})
        Tween(XBar2, 0.15, nil, nil, {BackgroundColor3 = Theme.Accent, Rotation = 45})
    end)
    MinBtn.MouseLeave:Connect(function()
        Tween(XBar1, 0.15, nil, nil, {BackgroundColor3 = Window._theme.Text, Rotation = 45})
        Tween(XBar2, 0.15, nil, nil, {BackgroundColor3 = Window._theme.Text, Rotation = -45})
    end)
    local function ToggleMinimize()
        Window._minimized = not Window._minimized
        if Window._minimized then
            Tween(BlurObj, 0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Size = 0})
            Tween(MainFrame, 0.22, Enum.EasingStyle.Back, Enum.EasingDirection.In, {
                Size = UDim2.new(0, Window._baseWidth * 0.9, 0, 0),
                BackgroundTransparency = 1
            })
            task.delay(0.2, function()
                if Window._minimized then MainFrame.Visible = false end
            end)
        else
            MainFrame.Visible = true
            Tween(BlurObj, 0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {
                Size = Window._theme.UseBlur and 12 or 0
            })
            Tween(MainFrame, 0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                Size = UDim2.new(0, Window._baseWidth, 0, Window._baseHeight),
                BackgroundTransparency = Window._theme.WindowTrans
            })
        end
    end
    MinBtn.MouseButton1Click:Connect(ToggleMinimize)
    DynamicIsland.MouseButton1Click:Connect(ToggleMinimize)
    UserInputService.InputBegan:Connect(function(inp, gpe)
        if not gpe then
            if inp.KeyCode == MinimizeKey then
                ToggleMinimize()
            elseif inp.KeyCode == Enum.KeyCode.K and UserInputService:IsKeyDown(Enum.KeyCode.LeftControl) then
                if Window._minimized then ToggleMinimize() end
                SearchInput:CaptureFocus()
            end
            for _, kb in ipairs(Window._keybinds) do
                if kb.Key and inp.KeyCode == kb.Key then
                    task.spawn(kb.Trigger)
                end
            end
        end
    end)
    local Sidebar = Create("Frame", {
        Size = UDim2.new(0, 155, 1, -60),
        Position = UDim2.new(0, 10, 0, 50),
        BackgroundColor3 = Theme.SidebarBg,
        BackgroundTransparency = Theme.SidebarTrans,
        Parent = MainFrame
    }, {
        Create("UICorner", {CornerRadius = UDim.new(0, 11)})
    })
    local SidebarStroke = Create("UIStroke", {
        Color = Theme.Stroke,
        Thickness = 1,
        Transparency = Theme.StrokeTrans,
        Parent = Sidebar
    })
    local ActiveIndicator = Create("Frame", {
        Size = UDim2.new(0, 4, 0, 20),
        Position = UDim2.new(0, 5, 0, 15),
        BackgroundColor3 = Theme.Accent,
        ZIndex = 4,
        Parent = Sidebar
    }, {
        Create("UICorner", {CornerRadius = UDim.new(1, 0)})
    })
    local TabScroll = Create("ScrollingFrame", {
        Size = UDim2.new(1, 0, 1, 0),
        BackgroundTransparency = 1,
        BorderSizePixel = 0,
        ScrollBarThickness = 0,
        AutomaticCanvasSize = Enum.AutomaticSize.Y,
        CanvasSize = UDim2.new(0, 0, 0, 0),
        Parent = Sidebar
    }, {
        Create("UIListLayout", {
            Padding = UDim.new(0, 4),
            HorizontalAlignment = Enum.HorizontalAlignment.Center,
            SortOrder = Enum.SortOrder.LayoutOrder
        }),
        Create("UIPadding", {
            PaddingTop = UDim.new(0, 7),
            PaddingBottom = UDim.new(0, 7)
        })
    })
    local PageHolder = Create("Frame", {
        Size = UDim2.new(1, -180, 1, -60),
        Position = UDim2.new(0, 172, 0, 50),
        BackgroundTransparency = 1,
        ClipsDescendants = true,
        Parent = MainFrame
    })
    local NotifyScale = nil
    local function UpdateResponsiveScale()
        if not AutoScaleEnabled then
            WindowScale.Scale = 1
            return
        end
        local cam = workspace.CurrentCamera
        if not cam then return end
        local vp = cam.ViewportSize
        if vp.X <= 0 or vp.Y <= 0 then return end
        local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled
        if isMobile or vp.X < 920 then
            Sidebar.Size = UDim2.new(0, 132, 1, -56)
            PageHolder.Position = UDim2.new(0, 148, 0, 48)
            PageHolder.Size = UDim2.new(1, -156, 1, -56)
            SearchBar.Size = UDim2.new(0, 138, 0, 28)
            SearchBar.Position = UDim2.new(1, -376, 0.5, -14)
        else
            Sidebar.Size = UDim2.new(0, 155, 1, -60)
            PageHolder.Position = UDim2.new(0, 172, 0, 50)
            PageHolder.Size = UDim2.new(1, -180, 1, -60)
            SearchBar.Size = UDim2.new(0, 185, 0, 30)
            SearchBar.Position = UDim2.new(1, -430, 0.5, -15)
        end
        local maxWRatio = isMobile and 0.74 or 0.82
        local maxHRatio = isMobile and 0.68 or 0.78
        local scaleX = (vp.X * maxWRatio) / math.max(540, Window._baseWidth)
        local scaleY = (vp.Y * maxHRatio) / math.max(340, Window._baseHeight)
        local targetScale = math.clamp(math.min(scaleX, scaleY), 0.42, 0.95)
        WindowScale.Scale = targetScale
        IslandScale.Scale = math.clamp(targetScale * 1.05, 0.65, 1.0)
        if NotifyScale then
            NotifyScale.Scale = math.clamp(targetScale, 0.65, 0.95)
        end
        local halfW = (Window._baseWidth * targetScale) * 0.5
        local halfH = (Window._baseHeight * targetScale) * 0.5
        local curX = (MainFrame.Position.X.Scale * vp.X) + MainFrame.Position.X.Offset
        local curY = (MainFrame.Position.Y.Scale * vp.Y) + MainFrame.Position.Y.Offset
        local clampedX = math.clamp(curX, math.min(halfW + 8, vp.X * 0.5), math.max(vp.X - halfW - 8, vp.X * 0.5))
        local clampedY = math.clamp(curY, math.min(halfH + 8, vp.Y * 0.5), math.max(vp.Y - halfH - 8, vp.Y * 0.5))
        MainFrame.Position = UDim2.new(0, clampedX, 0, clampedY)
    end
    local ResizeGrip = BindFont(Create("TextButton", {
        AnchorPoint = Vector2.new(1, 1),
        Position = UDim2.new(1, -4, 1, -4),
        Size = UDim2.new(0, 18, 0, 18),
        BackgroundTransparency = 1,
        Text = "◢",
        TextSize = 11,
        TextColor3 = Theme.SubText,
        TextTransparency = 0.35,
        AutoButtonColor = false,
        ZIndex = 10,
        Parent = MainFrame
    }), "Bold")
    local resizing, resizeInput, resizeStart, startW, startH = false, nil, nil, 0, 0
    ResizeGrip.InputBegan:Connect(function(inp)
        if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
            resizing = true
            resizeStart = inp.Position
            startW = Window._baseWidth
            startH = Window._baseHeight
            inp.Changed:Connect(function()
                if inp.UserInputState == Enum.UserInputState.End then resizing = false end
            end)
        end
    end)
    ResizeGrip.InputChanged:Connect(function(inp)
        if inp.UserInputType == Enum.UserInputType.MouseMovement or inp.UserInputType == Enum.UserInputType.Touch then
            resizeInput = inp
        end
    end)
    UserInputService.InputChanged:Connect(function(inp)
        if inp == resizeInput and resizing then
            local scale = math.max(0.45, WindowScale.Scale)
            local delta = (inp.Position - resizeStart) / scale
            Window._baseWidth = math.clamp(startW + delta.X, 540, 920)
            Window._baseHeight = math.clamp(startH + delta.Y, 340, 620)
            MainFrame.Size = UDim2.new(0, Window._baseWidth, 0, Window._baseHeight)
        end
    end)
    local vpConn = nil
    local function BindCameraViewport()
        if vpConn then vpConn:Disconnect() end
        local cam = workspace.CurrentCamera
        if cam then
            vpConn = cam:GetPropertyChangedSignal("ViewportSize"):Connect(UpdateResponsiveScale)
            UpdateResponsiveScale()
        end
    end
    workspace:GetPropertyChangedSignal("CurrentCamera"):Connect(BindCameraViewport)
    BindCameraViewport()
    local function ApplySearchFilter()
        local query = string.lower(SearchInput.Text or "")
        local tab = Window._activeTab
        if not tab then return end
        for _, child in ipairs(tab._page:GetChildren()) do
            if child:IsA("GuiObject") and child:GetAttribute("SearchKey") then
                if query == "" then
                    child.Visible = true
                else
                    local key = string.lower(child:GetAttribute("SearchKey"))
                    child.Visible = string.find(key, query, 1, true) ~= nil
                end
            end
        end
    end
    SearchInput:GetPropertyChangedSignal("Text"):Connect(ApplySearchFilter)
    Window:OnThemeChange(function(th)
        Tween(DynamicIsland, 0.25, nil, nil, {BackgroundColor3 = th.WindowBg})
        Tween(IslandStroke, 0.25, nil, nil, {Color = th.Accent})
        Tween(IslandDot, 0.25, nil, nil, {TextColor3 = th.Accent})
        Tween(IslandTitle, 0.25, nil, nil, {TextColor3 = th.Text})
        Tween(IslandTelemetry, 0.25, nil, nil, {TextColor3 = th.SubText})
        Tween(MainFrame, 0.25, nil, nil, {BackgroundColor3 = th.WindowBg, BackgroundTransparency = th.WindowTrans})
        Tween(MainStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(TopLogo, 0.25, nil, nil, {ImageColor3 = th.Accent})
        Tween(TitleLbl, 0.25, nil, nil, {TextColor3 = th.Text})
        Tween(SubTitleLbl, 0.25, nil, nil, {TextColor3 = th.SubText})
        Tween(SearchBar, 0.25, nil, nil, {BackgroundColor3 = th.InputBg, BackgroundTransparency = th.InputTrans})
        Tween(SearchStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(SearchIcon, 0.25, nil, nil, {ImageColor3 = th.SubText})
        SearchInput.TextColor3 = th.Text
        SearchInput.PlaceholderColor3 = th.SubText
        Tween(FontQuickBtn, 0.25, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans, TextColor3 = th.Accent})
        Tween(FontQuickStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(StyleQuickBtn, 0.25, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans, TextColor3 = th.Text})
        Tween(StyleQuickStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(ThemeQuickBtn, 0.25, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans})
        Tween(ThemeQuickStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(ThemeQuickIcon, 0.25, nil, nil, {ImageColor3 = th.Accent})
        Tween(MinBtn, 0.25, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans})
        Tween(MinBtnStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(XBar1, 0.25, nil, nil, {BackgroundColor3 = th.Text})
        Tween(XBar2, 0.25, nil, nil, {BackgroundColor3 = th.Text})
        Tween(Sidebar, 0.25, nil, nil, {BackgroundColor3 = th.SidebarBg, BackgroundTransparency = th.SidebarTrans})
        Tween(SidebarStroke, 0.25, nil, nil, {Color = th.Stroke, Transparency = th.StrokeTrans})
        Tween(ActiveIndicator, 0.25, nil, nil, {BackgroundColor3 = th.Accent})
        ResizeGrip.TextColor3 = th.SubText
    end)
    local NotifyContainer = Create("Frame", {
        AnchorPoint = Vector2.new(1, 1),
        Size = UDim2.new(0, 275, 1, -24),
        Position = UDim2.new(1, -12, 1, -12),
        BackgroundTransparency = 1,
        Parent = ScreenGui
    }, {
        Create("UIListLayout", {
            Padding = UDim.new(0, 8),
            VerticalAlignment = Enum.VerticalAlignment.Bottom,
            HorizontalAlignment = Enum.HorizontalAlignment.Right
        })
    })
    NotifyScale = Create("UIScale", {
        Scale = math.clamp(WindowScale.Scale, 0.68, 0.95),
        Parent = NotifyContainer
    })
    function Window:Notify(nCfg)
        nCfg = nCfg or {}
        local nTitle = tostring(nCfg.Title or "Notification")
        local nContent = tostring(nCfg.Content or nCfg.Description or "")
        local nDuration = tonumber(nCfg.Duration) or 3.5
        local th = self._theme
        local Card = Create("Frame", {
            Size = UDim2.new(1, 0, 0, 58),
            BackgroundColor3 = th.WindowBg,
            BackgroundTransparency = math.clamp(th.WindowTrans - 0.05, 0.05, 0.35),
            ClipsDescendants = true,
            Parent = NotifyContainer
        }, {
            Create("UICorner", {CornerRadius = UDim.new(0, 10)}),
            Create("UIStroke", {Color = th.Accent, Thickness = 1.2, Transparency = 0.25})
        })
        local IconImg = Create("ImageLabel", {
            Size = UDim2.new(0, 16, 0, 16),
            Position = UDim2.new(0, 12, 0, 11),
            BackgroundTransparency = 1,
            ImageColor3 = th.Accent,
            Parent = Card
        })
        ApplyWindIcon(IconImg, nCfg.Icon or "bell")
        BindFont(Create("TextLabel", {
            Size = UDim2.new(1, -42, 0, 17),
            Position = UDim2.new(0, 34, 0, 8),
            BackgroundTransparency = 1,
            Text = nTitle,
            TextSize = 12,
            TextColor3 = th.Text,
            TextXAlignment = Enum.TextXAlignment.Left,
            Parent = Card
        }), "Bold")
        BindFont(Create("TextLabel", {
            Size = UDim2.new(1, -42, 0, 26),
            Position = UDim2.new(0, 34, 0, 25),
            BackgroundTransparency = 1,
            Text = nContent,
            TextSize = 10,
            TextColor3 = th.SubText,
            TextWrapped = true,
            TextXAlignment = Enum.TextXAlignment.Left,
            TextYAlignment = Enum.TextYAlignment.Top,
            Parent = Card
        }), "Regular")
        local ProgBar = Create("Frame", {
            Size = UDim2.new(1, 0, 0, 3),
            Position = UDim2.new(0, 0, 1, -3),
            BackgroundColor3 = th.Accent,
            BorderSizePixel = 0,
            Parent = Card
        })
        Tween(ProgBar, nDuration, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, {Size = UDim2.new(0, 0, 0, 3)})
        task.delay(nDuration, function()
            Tween(Card, 0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.In, {
                Size = UDim2.new(1, 0, 0, 0),
                BackgroundTransparency = 1
            })
            task.wait(0.26)
            if Card then Card:Destroy() end
        end)
    end
    function Window:AddTab(tCfg)
        tCfg = tCfg or {}
        local tabTitle = tostring(tCfg.Title or "Tab")
        local tabIcon = tostring(tCfg.Icon or "layers")
        local tabIndex = #self._tabs + 1
        local TabBtn = Create("TextButton", {
            Size = UDim2.new(1, -14, 0, 34),
            BackgroundColor3 = self._theme.CardBg,
            BackgroundTransparency = 1,
            Text = "",
            AutoButtonColor = false,
            LayoutOrder = tabIndex,
            Parent = TabScroll
        }, {
            Create("UICorner", {CornerRadius = UDim.new(0, 8)})
        })
        local TIcon = Create("ImageLabel", {
            Size = UDim2.new(0, 16, 0, 16),
            Position = UDim2.new(0, 11, 0.5, -8),
            BackgroundTransparency = 1,
            ImageColor3 = self._theme.SubText,
            Parent = TabBtn
        })
        ApplyWindIcon(TIcon, tabIcon)
        local TLbl = BindFont(Create("TextLabel", {
            Size = UDim2.new(1, -36, 1, 0),
            Position = UDim2.new(0, 33, 0, 0),
            BackgroundTransparency = 1,
            Text = tabTitle,
            TextSize = 12,
            TextColor3 = self._theme.SubText,
            TextXAlignment = Enum.TextXAlignment.Left,
            TextTruncate = Enum.TextTruncate.AtEnd,
            Parent = TabBtn
        }), "Medium")
        local Page = Create("ScrollingFrame", {
            Size = UDim2.new(1, 0, 1, 0),
            Position = UDim2.new(0, 0, 0, 0),
            BackgroundTransparency = 1,
            BorderSizePixel = 0,
            ScrollBarThickness = 3,
            ScrollBarImageColor3 = self._theme.Accent,
            AutomaticCanvasSize = Enum.AutomaticSize.Y,
            CanvasSize = UDim2.new(0, 0, 0, 0),
            Visible = false,
            Parent = PageHolder
        }, {
            Create("UIListLayout", {
                Padding = UDim.new(0, 7),
                SortOrder = Enum.SortOrder.LayoutOrder
            }),
            Create("UIPadding", {
                PaddingTop = UDim.new(0, 3),
                PaddingBottom = UDim.new(0, 12),
                PaddingLeft = UDim.new(0, 2),
                PaddingRight = UDim.new(0, 8)
            })
        })
        local TabObj = {
            _btn = TabBtn,
            _icon = TIcon,
            _lbl = TLbl,
            _page = Page,
            _index = tabIndex,
            _order = 0
        }
        local function SelectThisTab()
            if Window._activeTab == TabObj then return end
            local th = Window._theme
            for _, other in ipairs(Window._tabs) do
                other._page.Visible = false
                Tween(other._btn, 0.22, nil, nil, {BackgroundTransparency = 1})
                Tween(other._icon, 0.22, nil, nil, {ImageColor3 = th.SubText})
                Tween(other._lbl, 0.22, nil, nil, {TextColor3 = th.SubText})
                BindFont(other._lbl, "Medium")
            end
            Window._activeTab = TabObj
            BindFont(TabObj._lbl, "Bold")
            Tween(TabBtn, 0.25, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans})
            Tween(TIcon, 0.25, nil, nil, {ImageColor3 = th.Accent})
            Tween(TLbl, 0.25, nil, nil, {TextColor3 = th.Text})
            local targetY = 7 + (tabIndex - 1) * 38 + 7
            Tween(ActiveIndicator, 0.32, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                Position = UDim2.new(0, 4, 0, targetY)
            })
            Page.Position = UDim2.new(0, 0, 0, 16)
            Page.Visible = true
            Tween(Page, 0.28, Enum.EasingStyle.Quart, Enum.EasingDirection.Out, {
                Position = UDim2.new(0, 0, 0, 0)
            })
            ApplySearchFilter()
        end
        TabBtn.MouseButton1Click:Connect(SelectThisTab)
        Window:OnThemeChange(function(th)
            Page.ScrollBarImageColor3 = th.Accent
            if Window._activeTab == TabObj then
                Tween(TabBtn, 0.2, nil, nil, {BackgroundColor3 = th.CardBg, BackgroundTransparency = th.CardTrans})
                Tween(TIcon, 0.2, nil, nil, {ImageColor3 = th.Accent})
                Tween(TLbl, 0.2, nil, nil, {TextColor3 = th.Text})
            else
                Tween(TIcon, 0.2, nil, nil, {ImageColor3 = th.SubText})
                Tween(TLbl, 0.2, nil, nil, {TextColor3 = th.SubText})
            end
        end)
        function TabObj:AddSection(title)
            self._order += 1
            local sTitle = type(title) == "table" and title.Title or tostring(title or "SECTION")
            local Holder = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 22),
                BackgroundTransparency = 1,
                LayoutOrder = self._order,
                Parent = Page
            })
            Holder:SetAttribute("SearchKey", sTitle)
            local Lbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, 0, 1, 0),
                Position = UDim2.new(0, 4, 0, 3),
                BackgroundTransparency = 1,
                Text = string.upper(sTitle),
                TextSize = 11,
                TextColor3 = Window._theme.Accent,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Holder
            }), "Bold")
            Window:OnThemeChange(function(th) Lbl.TextColor3 = th.Accent end)
            return Holder
        end
        TabObj.AddSeparator = TabObj.AddSection
        function TabObj:AddButton(bCfg)
            bCfg = bCfg or {}
            self._order += 1
            local bTitle = tostring(bCfg.Title or "Button")
            local bDesc = tostring(bCfg.Description or "")
            local callback = bCfg.Callback or function() end
            local Card = Create("TextButton", {
                Size = UDim2.new(1, 0, 0, bDesc ~= "" and 50 or 40),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                Text = "",
                AutoButtonColor = false,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", bTitle .. " " .. bDesc)
            RippleEffect(Card, Window._theme.Accent)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -48, 0, 17),
                Position = UDim2.new(0, 13, 0, bDesc ~= "" and 8 or 11),
                BackgroundTransparency = 1,
                Text = bTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local DLbl = nil
            if bDesc ~= "" then
                DLbl = BindFont(Create("TextLabel", {
                    Size = UDim2.new(1, -48, 0, 14),
                    Position = UDim2.new(0, 13, 0, 27),
                    BackgroundTransparency = 1,
                    Text = bDesc,
                    TextSize = 10,
                    TextColor3 = Window._theme.SubText,
                    TextXAlignment = Enum.TextXAlignment.Left,
                    Parent = Card
                }), "Regular")
            end
            local Arrow = Create("ImageLabel", {
                Size = UDim2.new(0, 15, 0, 15),
                Position = UDim2.new(1, -26, 0.5, -7.5),
                BackgroundTransparency = 1,
                ImageColor3 = Window._theme.Accent,
                Parent = Card
            })
            ApplyWindIcon(Arrow, bCfg.Icon or "chevron-right")
            Card.MouseEnter:Connect(function()
                Tween(Card, 0.18, nil, nil, {BackgroundColor3 = Window._theme.CardHover})
            end)
            Card.MouseLeave:Connect(function()
                Tween(Card, 0.18, nil, nil, {BackgroundColor3 = Window._theme.CardBg})
            end)
            Card.MouseButton1Click:Connect(function()
                Tween(Arrow, 0.12, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {Position = UDim2.new(1, -20, 0.5, -7.5)})
                task.delay(0.12, function()
                    Tween(Arrow, 0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Position = UDim2.new(1, -26, 0.5, -7.5)})
                end)
                task.spawn(callback)
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                if DLbl then DLbl.TextColor3 = th.SubText end
                Arrow.ImageColor3 = th.Accent
            end)
        end
        function TabObj:AddToggle(tgCfg)
            tgCfg = tgCfg or {}
            self._order += 1
            local tTitle = tostring(tgCfg.Title or "Toggle")
            local tDesc = tostring(tgCfg.Description or "")
            local flag = tgCfg.Flag
            local state = tgCfg.Default == true
            local customStyle = tgCfg.Style
            local callback = tgCfg.Callback or function() end
            if flag then Window._flags[flag] = state end
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, tDesc ~= "" and 50 or 40),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", tTitle .. " " .. tDesc)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -70, 0, 17),
                Position = UDim2.new(0, 13, 0, tDesc ~= "" and 8 or 11),
                BackgroundTransparency = 1,
                Text = tTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local DLbl = nil
            if tDesc ~= "" then
                DLbl = BindFont(Create("TextLabel", {
                    Size = UDim2.new(1, -70, 0, 14),
                    Position = UDim2.new(0, 13, 0, 27),
                    BackgroundTransparency = 1,
                    Text = tDesc,
                    TextSize = 10,
                    TextColor3 = Window._theme.SubText,
                    TextXAlignment = Enum.TextXAlignment.Left,
                    Parent = Card
                }), "Regular")
            end
            local Track = Create("TextButton", {
                AnchorPoint = Vector2.new(1, 0.5),
                Position = UDim2.new(1, -13, 0.5, 0),
                Size = UDim2.new(0, 42, 0, 22),
                BackgroundColor3 = Window._theme.InputBg,
                Text = "",
                AutoButtonColor = false,
                Parent = Card
            })
            local TrackCorner = Create("UICorner", {CornerRadius = UDim.new(1, 0), Parent = Track})
            local TrackStroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1.2,
                Transparency = 0.25,
                Parent = Track
            })
            local Knob = Create("Frame", {
                AnchorPoint = Vector2.new(0, 0.5),
                Position = UDim2.new(0, 3, 0.5, 0),
                Size = UDim2.new(0, 16, 0, 16),
                BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                Parent = Track
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local CheckIcon = Create("ImageLabel", {
                AnchorPoint = Vector2.new(0.5, 0.5),
                Position = UDim2.new(0.5, 0, 0.5, 0),
                Size = UDim2.new(0, 0, 0, 0),
                BackgroundTransparency = 1,
                ImageColor3 = Color3.fromRGB(255, 255, 255),
                ImageTransparency = 1,
                Parent = Track
            })
            ApplyWindIcon(CheckIcon, "check")
            local function RenderToggle(animate)
                local th = Window._theme
                local activeStyle = customStyle or Window._toggleStyle
                local dur = animate and 0.24 or 0
                if activeStyle == "Checkbox" then
                    Knob.Visible = false
                    CheckIcon.Visible = true
                    Tween(Track, dur, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                        Size = UDim2.new(0, 22, 0, 22),
                        BackgroundColor3 = state and th.Accent or th.InputBg
                    })
                    Tween(TrackCorner, dur, nil, nil, {CornerRadius = UDim.new(0, 6)})
                    Tween(TrackStroke, dur, nil, nil, {Color = state and th.Accent or th.Stroke})
                    Tween(CheckIcon, dur, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                        Size = state and UDim2.new(0, 14, 0, 14) or UDim2.new(0, 4, 0, 4),
                        ImageTransparency = state and 0 or 1
                    })
                else
                    CheckIcon.Visible = false
                    Knob.Visible = true
                    Tween(Track, dur, Enum.EasingStyle.Quart, Enum.EasingDirection.Out, {
                        Size = UDim2.new(0, 42, 0, 22),
                        BackgroundColor3 = state and th.Accent or th.InputBg
                    })
                    Tween(TrackCorner, dur, nil, nil, {CornerRadius = UDim.new(1, 0)})
                    Tween(TrackStroke, dur, nil, nil, {Color = state and th.Accent or th.Stroke})
                    Tween(Knob, dur, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                        Position = state and UDim2.new(1, -19, 0.5, 0) or UDim2.new(0, 3, 0.5, 0),
                        BackgroundColor3 = state and Color3.fromRGB(255, 255, 255) or th.SubText
                    })
                end
            end
            RenderToggle(false)
            local ToggleController = {}
            function ToggleController:SetValue(val)
                state = (val == true)
                if flag then Window._flags[flag] = state end
                RenderToggle(true)
                task.spawn(callback, state)
            end
            if flag then
                Window._flagSetters[flag] = function(v) ToggleController:SetValue(v) end
            end
            Track.MouseButton1Click:Connect(function()
                ToggleController:SetValue(not state)
            end)
            table.insert(Window._toggleStyleListeners, function()
                RenderToggle(true)
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                if DLbl then DLbl.TextColor3 = th.SubText end
                RenderToggle(false)
            end)
            return ToggleController
        end
        function TabObj:AddSlider(sCfg)
            sCfg = sCfg or {}
            self._order += 1
            local sTitle = tostring(sCfg.Title or "Slider")
            local flag = sCfg.Flag
            local minVal = tonumber(sCfg.Min) or 0
            local maxVal = tonumber(sCfg.Max) or 100
            local curVal = math.clamp(tonumber(sCfg.Default) or minVal, minVal, maxVal)
            local suffix = tostring(sCfg.Suffix or "")
            local callback = sCfg.Callback or function() end
            if flag then Window._flags[flag] = curVal end
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 54),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", sTitle)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -96, 0, 17),
                Position = UDim2.new(0, 13, 0, 8),
                BackgroundTransparency = 1,
                Text = sTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local ValBadge = BindFont(Create("TextLabel", {
                Size = UDim2.new(0, 72, 0, 19),
                Position = UDim2.new(1, -85, 0, 7),
                BackgroundColor3 = Window._theme.InputBg,
                BackgroundTransparency = 0.2,
                Text = tostring(curVal) .. suffix,
                TextSize = 11,
                TextColor3 = Window._theme.Accent,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 6)})
            }), "Mono")
            local Rail = Create("TextButton", {
                Size = UDim2.new(1, -26, 0, 6),
                Position = UDim2.new(0, 13, 0, 36),
                BackgroundColor3 = Window._theme.InputBg,
                Text = "",
                AutoButtonColor = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local Fill = Create("Frame", {
                Size = UDim2.new((curVal - minVal) / math.max(1, maxVal - minVal), 0, 1, 0),
                BackgroundColor3 = Window._theme.Accent,
                Parent = Rail
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)}),
                Create("UIGradient", {
                    Color = ColorSequence.new(Window._theme.Accent, Window._theme.AccentSecondary)
                })
            })
            local HaloRing = Create("Frame", {
                AnchorPoint = Vector2.new(0.5, 0.5),
                Position = UDim2.new(1, 0, 0.5, 0),
                Size = UDim2.new(0, 0, 0, 0),
                BackgroundColor3 = Window._theme.Accent,
                BackgroundTransparency = 1,
                ZIndex = 3,
                Parent = Fill
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local HaloStroke = Create("UIStroke", {
                Color = Window._theme.Accent,
                Thickness = 1.6,
                Transparency = 1,
                Parent = HaloRing
            })
            local Knob = Create("Frame", {
                AnchorPoint = Vector2.new(0.5, 0.5),
                Position = UDim2.new(1, 0, 0.5, 0),
                Size = UDim2.new(0, 10, 0, 10),
                BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                ZIndex = 4,
                Parent = Fill
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local KnobStroke = Create("UIStroke", {
                Color = Window._theme.Accent,
                Thickness = 1.6,
                Parent = Knob
            })
            local InnerDot = Create("Frame", {
                AnchorPoint = Vector2.new(0.5, 0.5),
                Position = UDim2.new(0.5, 0, 0.5, 0),
                Size = UDim2.new(0, 0, 0, 0),
                BackgroundColor3 = Window._theme.Accent,
                ZIndex = 5,
                Parent = Knob
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)})
            })
            local dragging = false
            local function SetSliderValue(v)
                curVal = math.clamp(math.floor(tonumber(v) or minVal + 0.5), minVal, maxVal)
                if flag then Window._flags[flag] = curVal end
                ValBadge.Text = tostring(curVal) .. suffix
                Tween(Fill, 0.07, Enum.EasingStyle.Sine, Enum.EasingDirection.Out, {
                    Size = UDim2.new((curVal - minVal) / math.max(1, maxVal - minVal), 0, 1, 0)
                })
                task.spawn(callback, curVal)
            end
            if flag then Window._flagSetters[flag] = SetSliderValue end
            local function UpdateSliderFromInput(input)
                local railWidth = math.max(1, Rail.AbsoluteSize.X)
                local alpha = math.clamp((input.Position.X - Rail.AbsolutePosition.X) / railWidth, 0, 1)
                SetSliderValue(minVal + (maxVal - minVal) * alpha)
            end
            Rail.MouseEnter:Connect(function()
                if not dragging then
                    Tween(Knob, 0.16, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Size = UDim2.new(0, 13, 0, 13)})
                end
            end)
            Rail.MouseLeave:Connect(function()
                if not dragging then
                    Tween(Knob, 0.16, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Size = UDim2.new(0, 10, 0, 10)})
                end
            end)
            Rail.InputBegan:Connect(function(inp)
                if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
                    dragging = true
                    Tween(Knob, 0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {Size = UDim2.new(0, 17, 0, 17)})
                    Tween(KnobStroke, 0.2, nil, nil, {Thickness = 2.4})
                    Tween(InnerDot, 0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {Size = UDim2.new(0, 6, 0, 6)})
                    Tween(HaloRing, 0.24, Enum.EasingStyle.Back, Enum.EasingDirection.Out, {
                        Size = UDim2.new(0, 30, 0, 30),
                        BackgroundTransparency = 0.78
                    })
                    Tween(HaloStroke, 0.24, nil, nil, {Transparency = 0.2})
                    UpdateSliderFromInput(inp)
                end
            end)
            UserInputService.InputEnded:Connect(function(inp)
                if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
                    if dragging then
                        dragging = false
                        Tween(Knob, 0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Size = UDim2.new(0, 10, 0, 10)})
                        Tween(KnobStroke, 0.2, nil, nil, {Thickness = 1.6})
                        Tween(InnerDot, 0.18, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {Size = UDim2.new(0, 0, 0, 0)})
                        Tween(HaloRing, 0.22, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, {
                            Size = UDim2.new(0, 0, 0, 0),
                            BackgroundTransparency = 1
                        })
                        Tween(HaloStroke, 0.22, nil, nil, {Transparency = 1})
                    end
                end
            end)
            UserInputService.InputChanged:Connect(function(inp)
                if dragging and (inp.UserInputType == Enum.UserInputType.MouseMovement or inp.UserInputType == Enum.UserInputType.Touch) then
                    UpdateSliderFromInput(inp)
                end
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                ValBadge.BackgroundColor3 = th.InputBg
                ValBadge.TextColor3 = th.Accent
                Rail.BackgroundColor3 = th.InputBg
                Fill.BackgroundColor3 = th.Accent
                KnobStroke.Color = th.Accent
                InnerDot.BackgroundColor3 = th.Accent
                HaloRing.BackgroundColor3 = th.Accent
                HaloStroke.Color = th.Accent
            end)
            return {SetValue = SetSliderValue}
        end
        function TabObj:AddDropdown(dCfg)
            dCfg = dCfg or {}
            self._order += 1
            local dTitle = tostring(dCfg.Title or "Dropdown")
            local flag = dCfg.Flag
            local options = dCfg.Options or {}
            local isMulti = dCfg.Multi == true
            local callback = dCfg.Callback or function() end
            local selected = isMulti and {} or tostring(dCfg.Default or options[1] or "")
            if isMulti and type(dCfg.Default) == "table" then
                for _, v in ipairs(dCfg.Default) do selected[v] = true end
            end
            if flag then Window._flags[flag] = selected end
            local isOpen = false
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 42),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                ClipsDescendants = true,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", dTitle)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local HeaderBtn = Create("TextButton", {
                Size = UDim2.new(1, 0, 0, 42),
                BackgroundTransparency = 1,
                Text = "",
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(0.48, 0, 1, 0),
                Position = UDim2.new(0, 13, 0, 0),
                BackgroundTransparency = 1,
                Text = dTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = HeaderBtn
            }), "Bold")
            local SelectedLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(0.45, -34, 1, 0),
                Position = UDim2.new(0.52, 0, 0, 0),
                BackgroundTransparency = 1,
                Text = "",
                TextSize = 11,
                TextColor3 = Window._theme.Accent,
                TextXAlignment = Enum.TextXAlignment.Right,
                TextTruncate = Enum.TextTruncate.AtEnd,
                Parent = HeaderBtn
            }), "Medium")
            local Chevron = Create("ImageLabel", {
                Size = UDim2.new(0, 15, 0, 15),
                Position = UDim2.new(1, -26, 0.5, -7.5),
                BackgroundTransparency = 1,
                ImageColor3 = Window._theme.SubText,
                Parent = HeaderBtn
            })
            ApplyWindIcon(Chevron, "chevron-down")
            local FilterBox = BindFont(Create("TextBox", {
                Size = UDim2.new(1, -22, 0, 26),
                Position = UDim2.new(0, 11, 0, 45),
                BackgroundColor3 = Window._theme.InputBg,
                PlaceholderText = "🔍 Filter options...",
                PlaceholderColor3 = Window._theme.SubText,
                Text = "",
                TextSize = 10,
                TextColor3 = Window._theme.Text,
                ClearTextOnFocus = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 6)})
            }), "Regular")
            local ListScroll = Create("ScrollingFrame", {
                Size = UDim2.new(1, -22, 0, 118),
                Position = UDim2.new(0, 11, 0, 76),
                BackgroundTransparency = 1,
                BorderSizePixel = 0,
                ScrollBarThickness = 2,
                ScrollBarImageColor3 = Window._theme.Accent,
                AutomaticCanvasSize = Enum.AutomaticSize.Y,
                CanvasSize = UDim2.new(0, 0, 0, 0),
                Parent = Card
            }, {
                Create("UIListLayout", {Padding = UDim.new(0, 4)})
            })
            local function UpdateSelectedText()
                if isMulti then
                    local items = {}
                    for _, opt in ipairs(options) do
                        if selected[opt] then table.insert(items, opt) end
                    end
                    SelectedLbl.Text = #items > 0 and table.concat(items, ", ") or "None"
                else
                    SelectedLbl.Text = selected ~= "" and tostring(selected) or "Select..."
                end
            end
            local function RebuildOptions()
                for _, ch in ipairs(ListScroll:GetChildren()) do
                    if ch:IsA("TextButton") then ch:Destroy() end
                end
                local q = string.lower(FilterBox.Text or "")
                for _, opt in ipairs(options) do
                    local optStr = tostring(opt)
                    if q == "" or string.find(string.lower(optStr), q, 1, true) then
                        local isChosen = isMulti and (selected[optStr] == true) or (selected == optStr)
                        local OptBtn = BindFont(Create("TextButton", {
                            Size = UDim2.new(1, -4, 0, 26),
                            BackgroundColor3 = isChosen and Window._theme.Accent or Window._theme.InputBg,
                            BackgroundTransparency = isChosen and 0.78 or 0.25,
                            Text = "   " .. optStr,
                            TextSize = 11,
                            TextColor3 = isChosen and Window._theme.Accent or Window._theme.Text,
                            TextXAlignment = Enum.TextXAlignment.Left,
                            AutoButtonColor = false,
                            Parent = ListScroll
                        }, {
                            Create("UICorner", {CornerRadius = UDim.new(0, 6)})
                        }), isChosen and "Bold" or "Regular")
                        OptBtn.MouseButton1Click:Connect(function()
                            if isMulti then
                                selected[optStr] = not selected[optStr]
                                UpdateSelectedText()
                                RebuildOptions()
                                local out = {}
                                for k, v in pairs(selected) do if v then table.insert(out, k) end end
                                if flag then Window._flags[flag] = out end
                                task.spawn(callback, out)
                            else
                                selected = optStr
                                if flag then Window._flags[flag] = selected end
                                UpdateSelectedText()
                                RebuildOptions()
                                task.spawn(callback, selected)
                            end
                        end)
                    end
                end
            end
            FilterBox:GetPropertyChangedSignal("Text"):Connect(RebuildOptions)
            UpdateSelectedText()
            RebuildOptions()
            HeaderBtn.MouseButton1Click:Connect(function()
                isOpen = not isOpen
                Tween(Chevron, 0.22, nil, nil, {Rotation = isOpen and 180 or 0})
                local targetH = isOpen and math.min(204, 84 + #options * 30) or 42
                Tween(Card, 0.26, Enum.EasingStyle.Quart, Enum.EasingDirection.Out, {
                    Size = UDim2.new(1, 0, 0, targetH)
                })
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                SelectedLbl.TextColor3 = th.Accent
                Chevron.ImageColor3 = th.SubText
                FilterBox.BackgroundColor3 = th.InputBg
                FilterBox.TextColor3 = th.Text
                RebuildOptions()
            end)
            local DropController = {}
            function DropController:Refresh(newOptions, newDefault)
                options = newOptions or {}
                if newDefault ~= nil then selected = newDefault end
                UpdateSelectedText()
                RebuildOptions()
            end
            return DropController
        end
        function TabObj:AddMultiDropdown(mCfg)
            mCfg = mCfg or {}
            mCfg.Multi = true
            return self:AddDropdown(mCfg)
        end
        function TabObj:AddKeybind(kCfg)
            kCfg = kCfg or {}
            self._order += 1
            local kTitle = tostring(kCfg.Title or "Keybind")
            local currentKey = kCfg.Default or Enum.KeyCode.E
            local callback = kCfg.Callback or function() end
            local listening = false
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 40),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", kTitle)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -105, 1, 0),
                Position = UDim2.new(0, 13, 0, 0),
                BackgroundTransparency = 1,
                Text = kTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local KeyBtn = BindFont(Create("TextButton", {
                AnchorPoint = Vector2.new(1, 0.5),
                Position = UDim2.new(1, -13, 0.5, 0),
                Size = UDim2.new(0, 78, 0, 24),
                BackgroundColor3 = Window._theme.InputBg,
                Text = "[" .. tostring(currentKey.Name) .. "]",
                TextSize = 11,
                TextColor3 = Window._theme.Accent,
                AutoButtonColor = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 6)})
            }), "Mono")
            local kbEntry = {
                Key = currentKey,
                Trigger = function()
                    if not listening then callback(currentKey) end
                end
            }
            table.insert(Window._keybinds, kbEntry)
            KeyBtn.MouseButton1Click:Connect(function()
                listening = true
                KeyBtn.Text = "[Press...]"
            end)
            UserInputService.InputBegan:Connect(function(inp)
                if listening and inp.UserInputType == Enum.UserInputType.Keyboard then
                    currentKey = inp.KeyCode
                    kbEntry.Key = currentKey
                    KeyBtn.Text = "[" .. tostring(currentKey.Name) .. "]"
                    task.wait(0.05)
                    listening = false
                end
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                KeyBtn.BackgroundColor3 = th.InputBg
                KeyBtn.TextColor3 = th.Accent
            end)
        end
        function TabObj:AddColorPicker(cCfg)
            cCfg = cCfg or {}
            self._order += 1
            local cTitle = tostring(cCfg.Title or "Color Picker")
            local curColor = cCfg.Default or Color3.fromRGB(95, 215, 255)
            local callback = cCfg.Callback or function() end
            local h, s, v = curColor:ToHSV()
            local expanded = false
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 40),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                ClipsDescendants = true,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", cTitle)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -85, 0, 40),
                Position = UDim2.new(0, 13, 0, 0),
                BackgroundTransparency = 1,
                Text = cTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local SwatchBtn = Create("TextButton", {
                AnchorPoint = Vector2.new(1, 0),
                Position = UDim2.new(1, -13, 0, 8),
                Size = UDim2.new(0, 44, 0, 24),
                BackgroundColor3 = curColor,
                Text = "",
                AutoButtonColor = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 6)}),
                Create("UIStroke", {Color = Color3.fromRGB(255, 255, 255), Thickness = 1, Transparency = 0.4})
            })
            local HueBar = Create("TextButton", {
                Size = UDim2.new(1, -26, 0, 13),
                Position = UDim2.new(0, 13, 0, 48),
                BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                Text = "",
                AutoButtonColor = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)}),
                Create("UIGradient", {
                    Color = ColorSequence.new({
                        ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 0, 0)),
                        ColorSequenceKeypoint.new(0.17, Color3.fromRGB(255, 255, 0)),
                        ColorSequenceKeypoint.new(0.33, Color3.fromRGB(0, 255, 0)),
                        ColorSequenceKeypoint.new(0.50, Color3.fromRGB(0, 255, 255)),
                        ColorSequenceKeypoint.new(0.67, Color3.fromRGB(0, 0, 255)),
                        ColorSequenceKeypoint.new(0.83, Color3.fromRGB(255, 0, 255)),
                        ColorSequenceKeypoint.new(1.00, Color3.fromRGB(255, 0, 0))
                    })
                })
            })
            local SatBar = Create("TextButton", {
                Size = UDim2.new(1, -26, 0, 13),
                Position = UDim2.new(0, 13, 0, 68),
                BackgroundColor3 = Color3.fromRGB(255, 255, 255),
                Text = "",
                AutoButtonColor = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(1, 0)}),
                Create("UIGradient", {
                    Color = ColorSequence.new(Color3.fromRGB(255, 255, 255), Color3.fromHSV(h, 1, 1))
                })
            })
            local function ApplyHSV()
                curColor = Color3.fromHSV(h, s, v)
                SwatchBtn.BackgroundColor3 = curColor
                task.spawn(callback, curColor)
            end
            SwatchBtn.MouseButton1Click:Connect(function()
                expanded = not expanded
                Tween(Card, 0.24, Enum.EasingStyle.Quart, Enum.EasingDirection.Out, {
                    Size = UDim2.new(1, 0, 0, expanded and 92 or 40)
                })
            end)
            HueBar.MouseButton1Down:Connect(function(x)
                h = math.clamp((x - HueBar.AbsolutePosition.X) / math.max(1, HueBar.AbsoluteSize.X), 0, 1)
                ApplyHSV()
            end)
            SatBar.MouseButton1Down:Connect(function(x)
                s = math.clamp((x - SatBar.AbsolutePosition.X) / math.max(1, SatBar.AbsoluteSize.X), 0, 1)
                ApplyHSV()
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
            end)
        end
        function TabObj:AddTextbox(tbCfg)
            tbCfg = tbCfg or {}
            self._order += 1
            local tTitle = tostring(tbCfg.Title or "Input")
            local placeholder = tostring(tbCfg.Placeholder or "Type here...")
            local defaultText = tostring(tbCfg.Default or "")
            local callback = tbCfg.Callback or function() end
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, 42),
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", tTitle)
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local TLbl = BindFont(Create("TextLabel", {
                Size = UDim2.new(0.5, 0, 1, 0),
                Position = UDim2.new(0, 13, 0, 0),
                BackgroundTransparency = 1,
                Text = tTitle,
                TextSize = 12,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Bold")
            local Box = BindFont(Create("TextBox", {
                Size = UDim2.new(0.45, -15, 0, 26),
                Position = UDim2.new(0.55, 0, 0.5, -13),
                BackgroundColor3 = Window._theme.InputBg,
                PlaceholderText = placeholder,
                PlaceholderColor3 = Window._theme.SubText,
                Text = defaultText,
                TextSize = 11,
                TextColor3 = Window._theme.Text,
                ClearTextOnFocus = false,
                Parent = Card
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 6)})
            }), "Regular")
            Box.FocusLost:Connect(function()
                task.spawn(callback, Box.Text)
            end)
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.CardBg
                Card.BackgroundTransparency = th.CardTrans
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                TLbl.TextColor3 = th.Text
                Box.BackgroundColor3 = th.InputBg
                Box.TextColor3 = th.Text
                Box.PlaceholderColor3 = th.SubText
            end)
        end
        function TabObj:AddConsole(conCfg)
            conCfg = conCfg or {}
            self._order += 1
            local cTitle = tostring(conCfg.Title or "Live Activity Console")
            local height = tonumber(conCfg.Height) or 130
            local Card = Create("Frame", {
                Size = UDim2.new(1, 0, 0, height),
                BackgroundColor3 = Window._theme.InputBg,
                BackgroundTransparency = 0.15,
                LayoutOrder = self._order,
                Parent = Page
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            Card:SetAttribute("SearchKey", cTitle .. " Console Logs")
            local Stroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = Card
            })
            local Header = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -20, 0, 22),
                Position = UDim2.new(0, 11, 0, 4),
                BackgroundTransparency = 1,
                Text = "▸ " .. cTitle,
                TextSize = 11,
                TextColor3 = Window._theme.Accent,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = Card
            }), "Mono")
            local LogScroll = Create("ScrollingFrame", {
                Size = UDim2.new(1, -20, 1, -32),
                Position = UDim2.new(0, 10, 0, 26),
                BackgroundTransparency = 1,
                BorderSizePixel = 0,
                ScrollBarThickness = 2,
                AutomaticCanvasSize = Enum.AutomaticSize.Y,
                CanvasSize = UDim2.new(0, 0, 0, 0),
                Parent = Card
            }, {
                Create("UIListLayout", {Padding = UDim.new(0, 3)})
            })
            local ConsoleCtrl = {}
            function ConsoleCtrl:Log(msg, level)
                local color = Window._theme.Text
                if level == "SUCCESS" then color = Color3.fromRGB(74, 222, 128)
                elseif level == "WARN" then color = Color3.fromRGB(250, 204, 21)
                elseif level == "ERROR" then color = Color3.fromRGB(248, 113, 113) end
                BindFont(Create("TextLabel", {
                    Size = UDim2.new(1, 0, 0, 15),
                    BackgroundTransparency = 1,
                    Text = string.format("[%s] %s", os.date("%H:%M:%S"), tostring(msg)),
                    TextSize = 10,
                    TextColor3 = color,
                    TextXAlignment = Enum.TextXAlignment.Left,
                    Parent = LogScroll
                }), "Mono")
            end
            function ConsoleCtrl:Clear()
                for _, c in ipairs(LogScroll:GetChildren()) do
                    if c:IsA("TextLabel") then c:Destroy() end
                end
            end
            Window:OnThemeChange(function(th)
                Card.BackgroundColor3 = th.InputBg
                Stroke.Color = th.Stroke
                Stroke.Transparency = th.StrokeTrans
                Header.TextColor3 = th.Accent
            end)
            return ConsoleCtrl
        end
        table.insert(self._tabs, TabObj)
        if #self._tabs == 1 then
            SelectThisTab()
        end
        return TabObj
    end
    function Window:AddInfoTab(infoCfg)
        infoCfg = infoCfg or {}
        local Tab = self:AddTab({
            Title = infoCfg.Title or "Info",
            Icon = infoCfg.Icon or "info"
        })
        local placeId = infoCfg.PlaceId or game.PlaceId
        local gameTitle = infoCfg.GameName or "Loading Game Name..."
        local HeroCard = Create("Frame", {
            Size = UDim2.new(1, 0, 0, 136),
            BackgroundColor3 = self._theme.CardBg,
            BackgroundTransparency = self._theme.CardTrans,
            ClipsDescendants = true,
            LayoutOrder = 1,
            Parent = Tab._page
        }, {
            Create("UICorner", {CornerRadius = UDim.new(0, 11)})
        })
        HeroCard:SetAttribute("SearchKey", "Game Info Thumbnail Banner Server")
        local HeroStroke = Create("UIStroke", {
            Color = self._theme.Stroke,
            Thickness = 1.2,
            Transparency = self._theme.StrokeTrans,
            Parent = HeroCard
        })
        Create("ImageLabel", {
            Size = UDim2.new(1, 0, 1, 0),
            BackgroundTransparency = 1,
            Image = string.format("rbxthumb://type=GameThumbnail&id=%d&w=768&h=432", placeId),
            ScaleType = Enum.ScaleType.Crop,
            ImageTransparency = 0.25,
            Parent = HeroCard
        }, {
            Create("UICorner", {CornerRadius = UDim.new(0, 11)}),
            Create("UIGradient", {
                Rotation = 90,
                Color = ColorSequence.new(Color3.fromRGB(255, 255, 255), Color3.fromRGB(10, 12, 18)),
                Transparency = NumberSequence.new({
                    NumberSequenceKeypoint.new(0, 0.35),
                    NumberSequenceKeypoint.new(0.65, 0.2),
                    NumberSequenceKeypoint.new(1, 0.02)
                })
            })
        })
        Create("ImageLabel", {
            Size = UDim2.new(0, 52, 0, 52),
            Position = UDim2.new(0, 14, 1, -64),
            BackgroundColor3 = self._theme.InputBg,
            Image = string.format("rbxthumb://type=GameIcon&id=%d&w=150&h=150", placeId),
            Parent = HeroCard
        }, {
            Create("UICorner", {CornerRadius = UDim.new(0, 9)}),
            Create("UIStroke", {Color = self._theme.Accent, Thickness = 1.5})
        })
        local GameNameLbl = BindFont(Create("TextLabel", {
            Size = UDim2.new(1, -190, 0, 20),
            Position = UDim2.new(0, 78, 1, -60),
            BackgroundTransparency = 1,
            Text = gameTitle,
            TextSize = 15,
            TextColor3 = Color3.fromRGB(255, 255, 255),
            TextXAlignment = Enum.TextXAlignment.Left,
            TextTruncate = Enum.TextTruncate.AtEnd,
            Parent = HeroCard
        }), "Bold")
        BindFont(Create("TextLabel", {
            Size = UDim2.new(1, -190, 0, 15),
            Position = UDim2.new(0, 78, 1, -38),
            BackgroundTransparency = 1,
            Text = string.format("Place ID: %d  •  Player: @%s", placeId, LocalPlayer.Name),
            TextSize = 10,
            TextColor3 = Color3.fromRGB(210, 220, 240),
            TextXAlignment = Enum.TextXAlignment.Left,
            Parent = HeroCard
        }), "Medium")
        if not infoCfg.GameName then
            task.spawn(function()
                local ok, info = pcall(function()
                    return MarketplaceService:GetProductInfo(placeId)
                end)
                if ok and info and info.Name then
                    GameNameLbl.Text = info.Name
                end
            end)
        end
        local GridContainer = Create("Frame", {
            Size = UDim2.new(1, 0, 0, 0),
            AutomaticSize = Enum.AutomaticSize.Y,
            BackgroundTransparency = 1,
            LayoutOrder = 2,
            Parent = Tab._page
        }, {
            Create("UIGridLayout", {
                CellSize = UDim2.new(0.5, -5, 0, 68),
                CellPadding = UDim2.new(0, 8, 0, 8),
                SortOrder = Enum.SortOrder.LayoutOrder
            })
        })
        GridContainer:SetAttribute("SearchKey", "Stats Info Metrics FPS Ping Custom")
        Tab._order = 3
        function Tab:AddStatCard(cardCfg)
            cardCfg = cardCfg or {}
            local cTitle = tostring(cardCfg.Title or "Stat")
            local cVal = tostring(cardCfg.Value or "0")
            local cSub = tostring(cardCfg.SubText or "")
            local cIcon = tostring(cardCfg.Icon or "activity")
            local SCard = Create("Frame", {
                BackgroundColor3 = Window._theme.CardBg,
                BackgroundTransparency = Window._theme.CardTrans,
                Parent = GridContainer
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 9)})
            })
            local SStroke = Create("UIStroke", {
                Color = Window._theme.Stroke,
                Thickness = 1,
                Transparency = Window._theme.StrokeTrans,
                Parent = SCard
            })
            local IconBadge = Create("Frame", {
                Size = UDim2.new(0, 34, 0, 34),
                Position = UDim2.new(0, 11, 0.5, -17),
                BackgroundColor3 = Window._theme.InputBg,
                BackgroundTransparency = 0.2,
                Parent = SCard
            }, {
                Create("UICorner", {CornerRadius = UDim.new(0, 8)})
            })
            local SIcon = Create("ImageLabel", {
                Size = UDim2.new(0, 17, 0, 17),
                Position = UDim2.new(0.5, -8.5, 0.5, -8.5),
                BackgroundTransparency = 1,
                ImageColor3 = Window._theme.Accent,
                Parent = IconBadge
            })
            ApplyWindIcon(SIcon, cIcon)
            local STLab = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -56, 0, 14),
                Position = UDim2.new(0, 52, 0, 9),
                BackgroundTransparency = 1,
                Text = cTitle,
                TextSize = 10,
                TextColor3 = Window._theme.SubText,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = SCard
            }), "Medium")
            local SVLab = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -56, 0, 20),
                Position = UDim2.new(0, 52, 0, 24),
                BackgroundTransparency = 1,
                Text = cVal,
                TextSize = 14,
                TextColor3 = Window._theme.Text,
                TextXAlignment = Enum.TextXAlignment.Left,
                TextTruncate = Enum.TextTruncate.AtEnd,
                Parent = SCard
            }), "Bold")
            local SSLab = BindFont(Create("TextLabel", {
                Size = UDim2.new(1, -56, 0, 12),
                Position = UDim2.new(0, 52, 0, 46),
                BackgroundTransparency = 1,
                Text = cSub,
                TextSize = 9,
                TextColor3 = Window._theme.Accent,
                TextXAlignment = Enum.TextXAlignment.Left,
                Parent = SCard
            }), "Regular")
            Window:OnThemeChange(function(th)
                SCard.BackgroundColor3 = th.CardBg
                SCard.BackgroundTransparency = th.CardTrans
                SStroke.Color = th.Stroke
                SStroke.Transparency = th.StrokeTrans
                IconBadge.BackgroundColor3 = th.InputBg
                SIcon.ImageColor3 = th.Accent
                STLab.TextColor3 = th.SubText
                SVLab.TextColor3 = th.Text
                SSLab.TextColor3 = th.Accent
            end)
            local StatController = {}
            function StatController:SetValue(newValue, newSubText)
                if newValue ~= nil then SVLab.Text = tostring(newValue) end
                if newSubText ~= nil then SSLab.Text = tostring(newSubText) end
            end
            return StatController
        end
        Window:OnThemeChange(function(th)
            HeroCard.BackgroundColor3 = th.CardBg
            HeroStroke.Color = th.Stroke
            HeroStroke.Transparency = th.StrokeTrans
        end)
        return Tab
    end
    return Window
end
return GlassLib
